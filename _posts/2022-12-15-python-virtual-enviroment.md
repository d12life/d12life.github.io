---
layout: post
author: d12life
title: Bài 3 - Hướng dẫn tạo môi trường ảo trong Python
---

Trong Python, môi trường ảo được sử dụng để cô lập môi trường của các dự án với nhau (ví dụ như trong trường hợp các dự án khác nhau yêu cầu các phiên bản khác nhau của cùng một thư viện). Môi trường ảo cho phép bạn cài đặt và quản lý các gói cài đặt một cách riêng rẽ và không xung đột với trình quản lý gói cài đặt của toàn hệ thống.

# 1. Virtual Environment
## 1.1. Cài đặt
Có hai công cụ chính được sử dụng để tạo môi trường ảo:
- virtualenv là công cụ tiêu chuẩn trong nhiều năm, có thể được sử dụng với cả Python 2 và 3.
- venv (pyvenv) được thêm vào thư viện chuẩn trong Python 3.3.
virtualenv có thể được cài đặt với trình quản lý gói cài pip bằng cách chạy lệnh pip install virtualenv. venv được tích hợp sẵn với Python 3, người dùng Debian/Ubuntu sẽ cần chạy sudo apt-get install python3-venv để làm cho nó hoạt động.

Cả hai công cụ đều giúp bạn tạo môi trường ảo cho project Python theo cách tương tự nhau. Bạn có thể sử dụng bất cứ công cụ nào muốn, trong trường hợp gặp vấn đề với 1 trong 2, bạn hoàn toàn có thể sử dụng công cụ còn lại.

**Lưu ý**: *venv* không cho phep tạo virtual enviroments với những phiên bản python khác nhau. Để làm điều này chúng ta cần cài đặt và sử dụng *virtualenv* package.
Please note that venv does not permit creating virtual environments with 

## 1.2. Tạo môi trường

Ở đây chúng ta sử dụng venv

```
python -m venv projectnamevenv
```

Trong đó *projectnamevenv* là tên folder chứa thông tin Virtual Environment cho dự án của bạn, bạn có thể đổi tên cho phù hợp hơn như /venv /virenv để dễ gợi nhớ hơn.


Activate môi trường vừa tạo trên Windows
```
> python -m venv venv
> venv\Scripts\activate
(venv) >
```

Đối với Linux
```
$ python -m venv venv
$ source venv/bin/activate
(venv) $
```

Bây giờ bạn sẽ thấy ở đầu dòng lệnh có thêm (venv), điều đó có nghĩa là môi trường của bạn đã được kích hoạt. Cả hai công cụ đều cài đặt sẵn *pip* và *setuptools* tuy nhiên *venv* không cài đặt sẵn *wheel*. Ngoài ra, các phiên bản mặc định có xu hướng chưa được cập nhật. Hãy nâng cấp chúng sau khi tạo môi trường mới:
```
$ pip install --upgrade pip setuptools wheel
```

# 2. Cài đặt Virtual Enviroment sử dụng Anaconda
## 2.1. Giới thiệu
Anaconda là 1 nền tảng mã nguồn mở về Khoa học Dữ liệu sử dụng ngôn ngữ lập trình Python thông dụng nhất hiện nay. Với hơn 25 triệu người dùng (theo thống kê tại trang chủ), Anaconda là giải pháp nhanh nhất và dễ nhất để các bạn có thể tìm hiểu Khoa học Dữ liệu với Python hoặc R trên Windows, Linux và Mac OS X.

Các bạn có thể tải Anaconda tương ứng với hệ điều hành các bạn sử dụng tại [đây](https://www.anaconda.com/products/distribution)

## 2.2. Conda, Miniconda, Anaconda
Với các bạn mới bắt đầu, khi tìm hiểu các tài liệu về *Anaconda* sẽ rất dễ gặp những cụm từ như Conda, Miniconda, thậm chí khi thi thoảng còn gặp những câu lệnh update đi liền nhau như sau:
```
conda update conda
conda update anaconda
```
Vậy thì *Conda, Miniconda, Anaconda* khác nhau như thế nào?

Hiểu 1 cách đơn giản, Conda là 1 công cụ quản lí môi trường (environments) và quản lý gói (packages). Nói nôm na, chúng ta sử dụng Conda như 1 công cụ dòng lệnh, đồng thời như 1 gói Python.

Miniconda và Anaconda có thể được biểu diễn như sau:
```
Miniconda = Python + conda
Anaconda = Python + conda + gói meta anaconda
```
## 2.3. Tạo môi trường ảo
Tạo môi trường
```
conda create -n projenv python=3.8
```
Ở đây, **-n** là viết tắt của **-name**, projenv là tên của môi trường. Để chọn phiên bản Python, ta sử dụng **python=**.

Kích hoạt môi trường
```
conda activate projenv
```

***Lưu ý***: Các công cụ tạo và quản lý Virtual Environment sẽ thêm và sử dụng 1 folder trong dự án của bạn để quản lý các gói cài đặt cũng như phiên bản Python (./venv như trong ví dụ trên), bạn không cần thiết phải quan tâm tới folder này, hãy nhớ đưa folder này vào .gitignore file trong trường hợp bạn sử dụng git.

# 3. Đóng gói và cài đặt lại

Bây giờ bạn muốn bê nguyên dự án bạn đang làm sang máy khác, bạn sẽ thấy là việc copy folder *./venv* ở trên không có tác dụng, điều đó xảy ra bởi vì mỗi môi trường ảo được tạo được gắn chặt với đường dẫn của project, phiên bản Python cài trên máy bạn và nhiều thông tin khác nữa. Để đóng gói và cài đặt lại môi trường trên máy mới, cách đơn giản nhất là sử dụng *pip* để *freeze* lại các gói cài sau đó cài đặt lại.

Trên máy cũ hoặc project folder cũ:
```
$ pip freeze > requirements.txt
```

Trên máy mới hoặc project folder mới (lưu ý tạo venv)
```
$ pip install -r requirements.txt
```

Bằng cách trên, các thông tin về gói cài đặt của dự án bao gồm tên gói cài đặt, phiên bản đang được cài sẽ được lưu lại trong file *requirements.txt*.

## 4. Tham khảo

1. [Python Virtual Environments: A Primer](https://realpython.com/python-virtual-environments-a-primer/)
2. [Python Virtual Environments in Five Minutes](https://chriswarrick.com/blog/2018/09/04/python-virtual-environments/)
3. [Pipenv & Virtual Environments](https://docs.python-guide.org/dev/virtualenvs/)
4. [https://zootopi.dev/tutorial/python/anaconda/](https://zootopi.dev/tutorial/python/anaconda/)