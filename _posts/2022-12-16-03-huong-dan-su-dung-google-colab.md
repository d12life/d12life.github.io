---
layout: post
author: d12life
title: Bài 6 - Hướng dẫn sử dụng google colab
---

**Colaboratory** hay còn gọi là **Google Colab**, là một sản phẩm từ Google Research, nó cho phép thực thi Python trên nền tảng đám mây, đặc biệt phù hợp với Data analysis, machine learning và giáo dục.

**Colab** không cần yêu cầu cài đặt hay cấu hình máy tính, mọi thứ có thể chạy thông qua trình duyệt, bạn có thể sử dụng tài nguyên máy tính từ CPU tốc độ cao và cả GPUs và cả TPUs đều được cung cấp cho bạn.

Sử dụng **Google Colab** có những lợi ích ưu việt như: sẵn sàng chạy Python ở bất kỳ thiết bị nào có kết nối Internet mà không cần cài đặt, chia sẻ và làm việc nhóm dễ dàng, sử dụng miễn phí GPU cho các dự án về AI.

# 1. Tại sao nên sử dụng Google Colab
## 1.1 Các thư viện được cài đặt sẵn
Phân phối Anaconda của **Jupyter Notebook** có một số dữ liệu được cài đặt sẵn như **Numpy, Pandas, Matplotlib**. Ngoài ra, Colab cũng cung cấp nhiều thư viện machine learning được cài đặt sẵn như **Keras, Pytorch, Tensorflow**.

## 1.2 Được lưu trên đám mây
Mọi thứ sẽ được lưu trữ trong cục bộ máy khi bạn lựa chọn Jupyter Notebook làm môi trường làm việc. Nếu bạn đề cao quyền riêng tư thì đây chắc chắn là một tính năng ưa thích của bạn.

Tuy nhiên, nếu bạn muốn máy tính của mình có thể truy cập được với tất cả thiết bị có đăng nhập Google, thì Google Colab là lựa chọn hàng đầu cho bạn. Vì tất cả Google Colab Notebook đều được lưu trong tài khoản Google Drive của bạn, giống như các tệp Google Docs và Google Sheets.

## 1.3 Sự hợp tác
Tính năng nổi trội khác mà Google Colab cung cấp chính là khả năng cộng tác. Vì giống như hợp tác trên tài liệu Google Docs, bạn có thể hợp tác với nhiều nhà phát triển bằng Google Colab Notebook. Bên cạnh đó, bạn cũng có thể chia sẻ công việc đã hoàn thành của mình với các nhà phát triển khác.

## 1.4 Sử dụng GPU và TPU miễn phí
Không cần phải suy nghĩ nhiều, khi chọn **Google Colab** thay vì `Jupyter Notebook`. Vì, Google Research  cho phép bạn sử dụng GPU và TPU chuyên dụng của họ cho các dự án machine learning cá nhân của bạn.

Đối với một số dự án, gia tốc GPU và TPU tạo ra sự khác biệt rất lớn ngay cả đối với một số dự án nhỏ.

## 1.5 Sự tổng quát
**Google Colab** là phiên bản chuyên dụng của Jupyter Notebook. Nó chạy trên đám mây và cung cấp tài nguyên điện toán miễn phí. Mối quan hệ giữa Ipython, Jupyter Notebook và Google Colab được hiển thị bên dưới:

![image](/assets/images/lesson_6/pasted-image-0-9-1.png)

# 2. Hướng dẫn sử dụng Google Colab
Để sử dụng **Colaboratory**, bạn phải có tài khoản Google, sau đó truy cập Colaboratory bằng tài khoản của bạn.

Đối với Jupyter Notebook, bạn có thể sử dụng Colaboratory để thực hiện các nhiệm vụ cụ thể trong một mô hình định hướng cell. Nếu bạn đã sử dụng Jupyter Notebook trước đây rồi, thì bạn sẽ thấy rõ sự tương đồng giữa Notebook và Colaboratory.

Dưới đây là các bước hướng dẫn bạn sử dụng **Google Colab**.

## 2.1 Lựa chọn GPU
Phần cứng mặc định của **Google Colab** là CPU hoặc nó có thể là GPU.

Để lựa chọn GPU, bạn hãy hấp vào `Edit` => `Notebook Setting` => `Hardware Accelerator` => `GPU`. Hoặc

Nhấp vào `Runtime` => `Hardware Accelerator`=> `GPU`

Kiểm tra thông tin GPU được cấp sử dụng lệnh
```
!nvidia-smi
```
Kết quả
![image](/assets/images/lesson_6/Screenshot%202023-01-04%20095652.png)

## 2.2 Running a Cell
1. Để đảm bảo thời gian chạy được kết nối. Notebook sẽ hiển thị màu xanh lá cây và **Connected** ở góc trên cùng bên phải.
2. Có nhiều tùy chọn thời gian chạy khác nhau trong **Runtime**.
3. Hoặc bạn có thể nhấn **Shift + Enter**.

## 2.3 Bash Commands
- Nhân bản kho lưu trữ Git
```
!git clone [git clone url]
```
- Lệnh thư mục *!ls, !mkdir*
```
!ls
```
- Tải xuống từ web
```
!wget [url] -p drive/[Folder Name]
```

## 2.4 Cài đặt thư viện
Các thư viện Python đều được cài đặt sẵn, nếu bạn muốn cài đặt các thư viện mới bạn có thể sử dụng cú pháp:
```
!pip install [package name]
```
hoặc
```
!apt-get install [package name]
```

## 2.5 Upload file từ local
```
from google.colab import files
uploaded = files.upload()
```
hoặc
```
for file in uploaded.keys():
  print('Uploaded file "{name}" with length {length} bytes'.format(name=file, length=len(uploaded[file])))
```

## 2.6 Gắn Google Drive vào Google Colab
```
from google.colab import drive
drive.mount('/content/drive')
```

## 2.7 Kiểm tra thông số kỹ thuật CPU và RAM
```
!cat /proc/cpuinfo
!cat /proc/meminfo
```

## 2.8 Kiểm tra thông số kỹ thuật GPU
```
from tensorflow.python.client import device_lib
device_lib.list_local_devices()
```

## 2.9 Auto connect khi thực hiện training trên google colab
Kết nối đến Google Colab thường bị disconnect sau 1 khoảng thời gian được quy định bởi Google. Khi bị disconnect chúng ta phải thực hiện lại tác vụ từ đầu. Để khắc phục chúng ta thực hiện như sau: Trên google chrome thực hiện `F12` ==> `Console` ==> `copy và paste đoạn code bên dưới vào console` ==> `Enter`
```
function ClickConnect(){
    console.log("Clicked on connect button"); 
    document.querySelector("colab-connect-button").click()
}
setInterval(ClickConnect,60000);
```

# 3. Tham khảo
[https://200lab.io/blog/google-colab-la-gi/#:~:text=Colaboratory%20hay%20c%C3%B2n%20g%E1%BB%8Di%20l%C3%A0,machine%20learning%20v%C3%A0%20gi%C3%A1o%20d%E1%BB%A5c](https://200lab.io/blog/google-colab-la-gi/#:~:text=Colaboratory%20hay%20c%C3%B2n%20g%E1%BB%8Di%20l%C3%A0,machine%20learning%20v%C3%A0%20gi%C3%A1o%20d%E1%BB%A5c)