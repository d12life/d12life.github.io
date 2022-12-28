---
layout: post
author: d12life
title: Bài 7 - Thực hành yolov7
---

Yolov7 là state-of-art model object detection release vào tháng 7/2022 bởi WongKinYiu and AlexeyAB. Nó được train để detect real-time 80 class của bộ dữ liệu COCO.
![image](/assets/images/lesson_7/637f2a024b36bcd05e4f9baa_performance.png)

# 1. Chuẩn bị
Kết nối Google Colab với Google Drive
```
from google.colab import drive
drive.mount('/content/drive')
```
Tạo file trên Google Colab và viết script auto reconnect Google Colab. Trên Google Chrome nhấn F12, chọn Console, copy và paste đoạn mã bên dưới vào cửa sổ Console, nhấn Enter.
```
function ClickConnect(){
    console.log("Clicked on connect button"); 
    document.querySelector("colab-connect-button").click()
}
setInterval(ClickConnect,60000)
```
Tải source code YOLOv7 về Google Drive, project yolov7 đã được clone từ https://github.com/WongKinYiu/yolov7 về https://github.com/d12life/yolov7.git để chúng ta có thể tùy chỉnh
```
# Clone source code YOLOv7 về google drive
%cd /content/drive/MyDrive/
!git clone https://github.com/d12life/yolov7.git
```
Sau chạy block code ở trên, trên Google Drive của các bạn sẽ xuất hiện thư mục yolov7.

Chuẩn bị dữ liệu: Ở đây chúng ta sử dụng bộ dữ liệu fire (nguồn miai.vn) để sử dụng cho bài thực hành này.
- Download bộ dữ liệu (đã được gán nhãn tại https://www.miai.vn/thu-vien-mi-ai/)
- Upload bộ dữ liệu firedata.zip vào thư mục yolov7/data trên Google Drive.

# 2. Nhận diện với pretrain model
Tải file weight pretrain: Trong thư mục yolov7 chúng ta tạo thư mục pretrain để chứa file yolov7 pretrain
```
%cd /content/drive/MyDrive/yolov7
!mkdir pretrain
%cd pretrain
!wget https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7.pt
```
Tải ảnh bất kỳ từ internet để thử nghiệm mô hình: Tạo thư mục test trong project yolov7 và download một số ảnh từ internet để thử nghiệm detect
```
%cd /content/drive/MyDrive/yolov7
!mkdir test
%cd test
!wget https://cdn.theculturetrip.com/wp-content/uploads/2017/11/15271255494_fcc90d3f9b_k.jpg
!wget https://cdnimgen.vietnamplus.vn/t620/uploaded/wbxx/2020_05_13/85896_3585300525545474_a1.jpg
!wget https://media-cdn-v2.laodong.vn/Storage/NewsPortal/2020/4/22/800234/Chay-Pho-Co-9.jpg
!wget https://i-vnexpress.vnecdn.net/2019/03/23/chay-1-3737-1553317413.jpg
```
Nhận diện thử với weight pretrain: Ảnh sau khi nhận diện được lưu tại thư mục runs/detect/exp
```
%cd /content/drive/MyDrive/yolov7
!python detect.py --weights pretrain/yolov7.pt --source test/15271255494_fcc90d3f9b_k.jpg
```
***Lưu ý***: Sau mỗi lần detect sẽ xuất hiện thêm một thư mục exp theo thứ tự tăng dần.
Xem ảnh đã nhận diện
```
from IPython.display import Image, display
display(Image(filename="/content/drive/MyDrive/yolov7/runs/detect/exp/15271255494_fcc90d3f9b_k.jpg"))
```
![image](/assets/images/lesson_7/15271255494_fcc90d3f9b_k.jpg)

# 3. Training YOLOv7 với custom data set
Cài đặt thư viện cần thiết để training model
```
%cd /content/drive/MyDrive/yolov7
!pip install -r requirements.txt
```
Thực hiện annotation dữ liệu fire với công cụ labelimg, dữ liệu sau khi được gán nhãn có dạng như sau
![image](/assets/images/lesson_7/935654ce-1185-4906-96bc-be74d7c5da46.png)

Giải nén dữ liệu để training model
```
%cd /content/drive/MyDrive/yolov7/data
!mkdir train_data
%cd train_data
!unzip ../firedata.zip
```

Tổ chức lại thư mục theo yêu cầu của YOLOv7
```
train
|- images
|- labels
test
|- images
|- labels

%cd /content/drive/MyDrive/yolov7/data/train_data
!mkdir train
!mkdir train/images
!mkdir train/labels
!mv *.jpg train/images
!mv *.txt train/labels
```

Khai báo file yam cho yolo biết
- Đường dẫn đến thư mục train, test (ở đây chúng ta dùng một tập dữ liệu chung cho cả train và test)
- Số lượng class chúng ta sẽ train qua biến nc (number of class)
- Tên của class qua biến names
```
%cd /content/drive/MyDrive/yolov7
!rm data/mydataset.yaml # nếu có
!echo 'train: ./data/train_data/train' >> data/mydataset.yaml
!echo 'val: ./data/train_data/train' >> data/mydataset.yaml
!echo 'nc: 1' >> data/mydataset.yaml
!echo "names: ['fire']" >> data/mydataset.yaml
```

Train yolo
- batch: Số batch, 8
- cfg: File config để training yolo
- epochs: Số epoch sẽ thực hiện training model
- data: Đường dân đến file mô tả dữ liệu chúng ta đã tạo ở trên
- weights: File pretrain chúng ta sử dụng để thực hiện transfer learning
```
%cd /content/drive/MyDrive/yolov7
!python train.py --batch 8 --cfg cfg/training/yolov7.yaml --epochs 200 --data data/mydataset.yaml --weights 'pretrain/yolov7.pt'
```

Nhận diện ảnh vừa train:
```
%cd /content/drive/MyDrive/yolov7
!python detect.py --weights /content/drive/MyDrive/yolov7/runs/train/exp/weights/best.pt --source test/Chay-Pho-Co-9.jpg --conf 0.2
```
***Lưu ý***: Nếu không thấy bounding box xuất hiện trên ảnh sau khi detect thì có thể confident của ảnh không đạt được ngưỡng cấu hình mặc định của yolo, để vẽ bounding bõ ta cần hạ cấu hình confident sử dụng tùy chọn *--conf*

Xem ảnh đã nhận diện
```
from IPython.display import Image, display
display(Image(filename="/content/drive/MyDrive/yolov7/runs/detect/exp2/Chay-Pho-Co-9.jpg"))
```
![image](/assets/images/lesson_7/fire_detect.jpg)

# 4. Tham khảo
1. https://www.analyticsvidhya.com/blog/2022/08/how-to-train-a-custom-object-detection-model-with-yolov7/
2. https://machinelearningprojects.net/train-yolov7-on-the-custom-dataset/