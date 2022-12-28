---
layout: post
author: d12life
title: Bài 5 - Gán nhãn dữ liệu và công cụ sử dụng
---
Để có dữ liệu sạch và có giá trị đối với các thuật toán thì dữ liệu cần được gán nhãn và chú giải bởi con người. Dưới đây là gợi ý về một số loại chú giải cho dữ liệu hình ảnh và các định dạng khác nhau của nhãn.

# 1. Tầm quan trọng của gán nhãn dữ liệu
Nếu bạn đưa cho đứa trẻ một quả cà chua và nói rằng đây là củ khoai tây, thì những lần sau đó, khi nhìn thấy cà chua, rất có thể đứa trẻ sẽ phân loại đó là khoai tây. Điều này tương tự đối với việc gán nhãn dữ liệu trong học máy có giám sát. Bởi mô hình học máy cũng học theo cách như vậy, bằng cách xem xét các ví dụ, kết quả của mô hình phụ thuộc vào các nhãn dữ liệu được cung cấp trong giai đoạn đào tạo.

Garbage In Garbage Out là một cụm từ thường được sử dụng trong cộng đồng học máy, có nghĩa là chất lượng của dữ liệu đào tạo quyết định đến chất lượng của mô hình, do đó, cũng phụ thuộc vào các chú thích được sử dụng để gán nhãn dữ liệu. Đây là một công việc đòi hỏi nhiều thao tác thủ công. Để có dữ liệu sạch và có giá trị đối với các thuật toán thì dữ liệu cần được gán nhãn và chú giải bởi con người. Dưới đây là gợi ý về một số loại chú giải cho dữ liệu hình ảnh, các định dạng khác nhau của nhãn, nhằm giúp bạn có được lựa chọn phù hợp và hoàn thành tốt tác vụ gán nhãn dữ liệu.

# 2. Các loại chú giải cho dữ liệu ảnh
**Bounding boxes**: là loại chú thích được sử dụng phổ biến nhất trong thị giác máy tính. Bounding boxes là các hộp hình chữ nhật dùng để xác định vị trí của đối tượng mục tiêu. Chúng có thể được xác định bằng tọa độ trục 𝑥 và 𝑦 ở góc trên bên trái và  góc dưới bên phải của hình chữ nhật. Hộp giới hạn thường được sử dụng trong các nhiệm vụ phát hiện và khoanh vùng đối tượng. 

![image](/assets/images/lesson_5/bd-box.jpeg.webp)

Bounding boxes thường được biểu diễn bằng hai tọa độ (x1, y1) và (x2, y2) hoặc bởi một tọa độ (x1, y1) và chiều rộng (w) và chiều cao (h) của hộp.

**Polygonal Segmentation** (Phân đoạn đa giác): Các đối tượng không phải lúc nào cũng có dạng hình chữ nhật. Với ý tưởng này, phân đoạn đa giác là một loại chú thích dữ liệu khác trong đó các đa giác phức tạp được sử dụng thay vì hình chữ nhật để xác định hình dạng và vị trí của đối tượng một cách chính xác.

![image](/assets/images/lesson_5/1_mvAz7lcEqusO24AyXyIxLQ.png.webp)

**Semantic Segmentation** (Phân đoạn theo ngữ nghĩa): là một chú thích pixel, trong đó mỗi pixel trong hình ảnh được gán cho một lớp. Mỗi pixel mang một ý nghĩa khác nhau. Phân đoạn ngữ nghĩa chủ yếu được sử dụng trong trường hợp bối cảnh môi trường là rất quan trọng. Ví dụ, nó được sử dụng trong ô tô tự lái và robot để giúp các mô hình hiểu rõ được môi trường mà chúng đang hoạt động. 

![image](/assets/images/lesson_5/Semantic-segmentation.webp)

**Instance segmentation**: Khác với Semantic Segmentation (phân đoạn theo từng lớp), instance segmentation là cách phân đoạn các vùng ảnh chi tiết đến từng đối tượng trong mỗi nhãn. Ví dụ, nếu trong ảnh có 5 người, thì với cách phân đoạn này, sẽ có 5 vùng khác nhau cho mỗi người. 

**Hình khối 3D**: Hình khối 3D tương tự như các hộp giới hạn với thông tin sâu hơn về đối tượng. Do đó, với hình khối 3D, bạn có thể có được hình ảnh đại diện 3D của đối tượng, cho phép hệ thống phân biệt các tính năng như thể tích và vị trí trong không gian 3D. Một trường hợp sử dụng của hình khối 3D là trong ô tô tự lái, nơi sử dụng thông tin về độ sâu để đo khoảng cách của các vật thể từ ô tô.

![image](/assets/images/lesson_5/3d.webp)

**Key-Point and Landmark**: Chú thích Key-Point and Landmark được sử dụng để phát hiện các đối tượng nhỏ và các biến thể hình dạng bằng cách tạo các chấm trên hình ảnh. Loại chú thích này rất hữu ích để phát hiện các đặc điểm khuôn mặt, nét mặt, cảm xúc, các bộ phận cơ thể người và tư

![image](/assets/images/lesson_5/key-point.webp)

**Lines and Splines**: là chú thích được tạo ra bằng cách sử dụng các lines và splines. Nó thường được sử dụng trong các phương tiện tự hành để phát hiện và nhận dạng làn đường.

![image](/assets/images/lesson_5/line.webp)

# 3. Các định dạng gán nhãn cho dữ liệu ảnh
- COCO: COCO có năm loại chú thích: phát hiện đối tượng, phát hiện điểm chính, phân đoạn nội dung, phân đoạn toàn cảnh và chú thích hình ảnh. Các chú thích được lưu trữ bằng JSON.
- Pascal VOC: Pascal VOC lưu trữ chú thích trong tệp XML. 
- YOLO: Ở định dạng ghi nhãn YOLO, một tệp .txt có cùng tên được tạo cho mỗi tệp hình ảnh trong cùng một thư mục. Mỗi tệp .txt chứa các chú thích cho tệp hình ảnh tương ứng, đó là lớp đối tượng, tọa độ đối tượng, chiều cao và chiều rộng (<object-class> <x> <y> <width> <height>).

# 4. Hướng dẫn sử dụng công cụ **labelImg**
**LabelImg** là một công cụ annotation được viết bằng ngôn ngữ Python và sử dụng Qt cho giao diện đồ họa.

Annotations được lưu theo định dạng XML của PASCAL VOC (định dạng được sử dụng bởi ImageNet). Bên cạnh đó nó cũng hỗ trợ định dạng YOLO và CreateML.
![image](/assets/images/lesson_5/labelImg1.jpg)

# 4.1 Cài đặt trên môi trường Windows
- **Bước 1**: Các bạn clone source code từ repo: https://github.com/tzutalin/labelImg.
- **Bước 2**: Cài đặt python (nếu trên máy đã có cài sẵn python thì bỏ qua bước này)
- **Bước 3**: Cài PyQt5 bằng cmd
```
pip install PyQt5
```
- **Bước 4**: Cài lxml
```
pip install lxml
```
- **Bước 5**: Copy các file cần thiết bằng cmd
```
pyrcc5 -o libs/resources.py resources.qrc
```
Vậy là xong, chạy file labelImg.py để bắt đầu gán nhãn cho ảnh.

## 4.2 Gán nhãn theo định dạng PascalVOC
1. Chạy file labelImg.py để launch chương trình.
2. Nhấp ‘Change default saved annotation folder’ trên Menu/File
3. Nhấp ‘Open Dir’
4. Nhấp ‘Create RectBox’
5. Nhấp và nhả chuột trái để chọn vùng cần annotate cho rect box
6. Chúng ta có thể sử dụng chuột phải để kéo rect box để sao chép hoặc di chuyển nó.

Annotation sẽ được lưu vào thư mục bạn đã chỉ định.

## 4.3 Gán nhãn theo định dạng YOLO
1. Trong thư mục `data/predefined_classes.txt` định nghĩa danh sách các lớp sẽ được sử dụng để training.
2. Chạy file labelImg.py để launch chương trình.
3. Nhấp vào nút “PascalVOC” ngay bên dưới nút “Save” trên toolbar để chuyển sang định dạng YOLO.
4. Chúng ta có thể sử dụng Open/OpenDIR để xử lý một hoặc nhiều ảnh. Khi xử lý xong một ảnh, nhấp save.

Một file txt theo định dạng YOLO cùng tên với file ảnh và một file có tên “classes.txt” sẽ được lưu trong cùng thư mục chứa ảnh. “classes.txt” định nghĩa danh sách tên lớp YOLO label tham chiếu.

***Lưu ý***: 
- Danh sách label của chúng ta không nên thay đổi trong quá trình gán nhãn. Khi chúng ta lưu một ảnh, classes.txt sẽ được update, trong khi annotations trước đó sẽ không được update.
- Chúng ta không nên sử dụng chức năng “default class” khi lưu ảnh với định dạng YOLO, nó sẽ không được tham chiếu.
- Khi lưu với định dạng YOLO, cờ “difficult” bị bỏ qua.

## 4.4. Tạo các lớp pre-defined
Chúng ta có thể edit file [data/predefined_classes.txt](https://github.com/heartexlabs/labelImg/blob/master/data/predefined_classes.txt) để load các lớp pre-defined.

## 4.5 Hotkeys

| Ctrl + u         | Load all of the images from a directory   |
| ---------------- | ----------------------------------------- |
| Ctrl + r         | Change the default annotation target dir  |
| Ctrl + s         | Save                                      |
| Ctrl + d         | Copy the current label and rect box       |
| Ctrl + Shift + d | Delete the current image                  |
| Space            | Flag the current image as verified        |
| w                | Create a rect box                         |
| d                | Next image                                |
| a                | Previous image                            |
| del              | Delete the selected rect box              |
| Ctrl++           | Zoom in                                   |
| Ctrl–            | Zoom out                                  |
| ↑→↓←             | Keyboard arrows to move selected rect box |

## 4.6 Verify Image
Khi nhấn phím cách, người dùng có thể đánh dấu ảnh đã xác minh, nền xanh sẽ xuất hiện. Điều này được sử dụng khi tạo tập dữ liệu tự động, sau đó người dùng có thể xem qua tất cả các ảnh và gắn cờ cho chúng thay vì chú thích chúng.

## 4.7 Difficult
Trường difficult được đặt thành 1 cho biết đối tượng đã được chú thích là "difficult", ví dụ: một đối tượng có thể nhìn thấy rõ ràng nhưng khó nhận ra nếu không sử dụng ngữ cảnh đáng kể. Theo cách triển khai mạng lưới thần kinh sâu của bạn, bạn có thể bao gồm hoặc loại trừ các đối tượng khó trong quá trình đào tạo.

## 4.8 How to reset the settings
Trong trường hợp có issue trong khi load các lớp (classes), chúng ta có thể thực hiện một trong 2 cách:
1. Nhấn Menu/File/Reset All
2. Remove the .labelImgSettings.pkl from your home directory. In Linux and Mac you can do:
rm ~/.labelImgSettings.pkl

# 5. Tham khảo
1. https://blog.vinbigdata.org/garbage-in-garbage-out-tu-goc-do-gan-nhan-du-lieu/
2. https://pypi.org/project/labelImg/