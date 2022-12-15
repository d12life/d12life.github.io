---
layout: post
author: d12life
title: Bài 3 - Tạo môi trường ảo để làm việc với Python
---

Trong Python, môi trường ảo được sử dụng để cô lập môi trường của các dự án với nhau (ví dụ như trong trường hợp các dự án khác nhau yêu cầu các phiên bản khác nhau của cùng một thư viện). Môi trường ảo cho phép bạn cài đặt và quản lý các gói cài đặt một cách riêng rẽ và không xung đột với trình quản lý gói cài đặt của toàn hệ thống.

# Cài đặt và tạo môi trường Virtual Environment
## Cài đặt

Có hai công cụ chính được sử dụng để tạo môi trường ảo:

- virtualenv là công cụ tiêu chuẩn trong nhiều năm, có thể được sử dụng với cả Python 2 và 3.
- venv (pyvenv) được thêm vào thư viện chuẩn trong Python 3.3.
virtualenv có thể được cài đặt với trình quản lý gói cài pip bằng cách chạy lệnh pip install virtualenv. venv được tích hợp sẵn với Python 3, người dùng Debian/Ubuntu sẽ cần chạy sudo apt-get install python3-venv để làm cho nó hoạt động.

Cả hai công cụ đều giúp bạn tạo môi trường ảo cho project Python theo cách tương tự nhau. Bạn có thể sử dụng bất cứ công cụ nào muốn, trong trường hợp gặp vấn đề với 1 trong 2, bạn hoàn toàn có thể sử dụng công cụ còn lại.

## Tạo môi trường:

Ở đây chúng ta sử dụng venv

```
python -m venv projectnamevenv
```

Trong đó projectnamevenv là tên folder chứa thông tin Virtual Environment cho dự án của bạn, bạn có thể đổi tên cho phù hợp hơn như /venv /virenv để dễ gợi nhớ hơn.

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

## Đóng gói và cài đặt lại

Bây giờ bạn muốn bê nguyên dự án bạn đang làm sang máy khác, bạn sẽ thấy là việc copy folder *./venv* ở trên không có tác dụng, điều đó xảy ra bởi vì mỗi môi trường ảo được tạo được gắn chặt với đường dẫn của project, phiên bản Python cài trên máy bạn và nhiều thông tin khác nữa. Để đóng gói và cài đặt lại môi trường trên máy mới, cách đơn giản nhất là sử dụng *pip* để *freeze* lại các gói cài sau đó cài đặt lại.

Trên máy cũ hoặc project folder cũ:
```
$ pip freeze > requirements.txt
```

Trên máy mới hoặc project folder mới
```
$ pip install -r requirements.txt
```

Bằng cách trên, các thông tin về gói cài đặt của dự án bao gồm tên gói cài đặt, phiên bản đang được cài sẽ được lưu lại trong file *requirements.txt*.

## Thêm một chút:

Các công cụ tạo và quản lý Virtual Environment sẽ thêm và sử dụng 1 folder trong dự án của bạn để quản lý các gói cài đặt cũng như phiên bản Python (./venv như trong ví dụ trên), bạn không cần thiết phải quan tâm tới folder này, hãy nhớ đưa folder này vào .gitignore file trong trường hợp bạn sử dụng git.

Nếu bạn là người sử dụng máy tính duy nhất, bạn có nên sử dụng môi trường ảo hay không? Câu trả lời là có, trong trường hợp bạn làm nhiều project khác nhau với các gói cài đặt khác nhau, môi trường ảo là cách đơn giản nhất để quản lý chúng.

## Xem thêm

[Python Virtual Environments: A Primer](https://realpython.com/python-virtual-environments-a-primer/)

[Python Virtual Environments in Five Minutes](https://chriswarrick.com/blog/2018/09/04/python-virtual-environments/)

[Pipenv & Virtual Environments](https://docs.python-guide.org/dev/virtualenvs/)