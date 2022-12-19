---
layout: post
author: d12life
title: Bài 4 - Giới thiệu công cụ ngrok
---
# 1. Giới thiệu và cài đặt ngrok
**ngrok** là một ứng dụng tạo ra một tunel từ máy bạn (desktop, localhost) đi qua hệ thống Firewall/Nat, giúp từ internet có thể truy cập vào máy trạm.

Bạn có thể dùng ngrok để có thể giúp từ ngoài internet truy cập vào một trang web (máy chủ http) đang chạy thử trên máy của bạn, mà không nhất thiết phải triển khai web nên một server thực sự.
![image](/assets/images/lesson_4/ngrok01.png)

**ngrok** có cho macOS, Windows, Linux - tải về tại [ngrok download](https://ngrok.com/download), sau khi tải về giải nén được file `ngrok` (ngrok.exe trên Windows)

Để gõ được lệnh `ngrok` bất kỳ đầu nên copy vào một thư mục có trong biến môi trường PATH, kiểm tra các thư mục đó bằng lệnh
```
echo $PATH
# Trên Windows thì gõ trong PowerShell
$env:Path
```

Để có hướng dẫn sử dụng lệnh `ngrok`, gõ:
```
ngrok help
```

**ngrok** cung cấp các gói: Free, Basic, Pro, Business. Trong đó gói miễn phí thì giới hạn tính năng như sau:
- Cho tạo các đường kết nối http/tcp với Url sinh ngẫu nhiên (không chọn Url được)
- Chỉ một tiến trình ngrok chạy trực tuyến
- Tối đa 4 đường hầm trên tiến trình
- 40 kết nối / phút

Chúng ta cần vào trang chủ https://dashboard.ngrok.com/, đăng ký và quản lý tài khoản của mình, tại đây sau khi đăng nhập, bạn vào mục Your Authtoken để lấy token đăng nhập
![image](/assets/images/lesson_4/ngrok03.png)

Sau khi có token đăng nhập, ví dụ ở đây là `1c1H3F3ibijIQZaohho51qVxlAQ_518Pvso9gbTmhxRQ19y75`, thì tiến hành gõ lệnh sau để kết nối tài khoản của bạn
```
ngrok authtoken 1c1H3F3ibijIQZaohho51qVxlAQ_518Pvso9gbTmhxRQ19y75
```
Giờ chúng ta đã có thể tạo ra các tunel để kết nối từ internet.

# 2. Sử dụng ngrok
Giả sử chúng ta có một website chạy trên máy local với địa chỉ truy cập là http://localhost:5000

Chúng ta sẽ dùng ngrok mở tunel để truy cập tới cổng 5000 trên máy local như sau
```
ngrok http 5000
```
![image](/assets/images/lesson_4/ngrok06.png)

Khi kết nối đang được duy trì, chúng ta có thể truy cập ứng dụng web trên local bằng url do ngrok cung cấp (http://e8f0a167.ngrok.io) từ máy bất kỳ trên internet.

# 3. **ngrok** Web Interface
**ngrok** cung cấp một trang quản quản lý, giám sát cho chúng ta ở địa chỉ http://127.0.0.1:4040/, tại đây chúng ta có thể biết các thông số, các kết nối đến web của bạn.

# 4. Đặt user/password khi của cập
Chúng ta có thể yêu cầu bên ngoài internet truy cập cần nhập user, password bằng lệnh sau (name:pass là user/pass người dùng cần nhập để truy cập đến web trong mạng local):
```
ngrok http -auth "name:pass" 5000
```

Thực hiện tương tự đối với các kết nối tcp
```
ngrok tcp 3306 # kết nối đến máy chủ mysql
```

# 5. Tham khảo
1. https://xuanthulab.net/su-dung-ngrok-de-truy-cap-tu-internet-vao-may-ca-nhan.html#:~:text=ngrok%20l%C3%A0%20m%E1%BB%99t%20%E1%BB%A9ng%20d%E1%BB%A5ng,truy%20c%E1%BA%ADp%20v%C3%A0o%20m%C3%A1y%20tr%E1%BA%A1m.