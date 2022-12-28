---
layout: post
author: d12life
title: Bài 9 - Hướng dẫn sử dụng công cụ wget
---

Wget là một công cụ máy tính được tạo bởi GNU Project. Bạn có thể sử dụng nó để lấy nội dung và tệp từ các máy chủ web khác nhau. Tên của nó là sự kết hợp của World Wide Web và từ `get`. Nó có hỗ trợ các giao thức như FTP, SFTP, HTTP và HTTPS.

# 1. Cài đặt
Ubuntu: ***sudo apt-get install wget***

CentOS: ***sudo yum install wget***

# 2. Hướng dẫn sử dụng
## 2.1 Tải về một tập tin
Một trong những lệnh wget cơ bản nhất là tải xuống một tệp và lưu trữ nó trên thư mục làm việc hiện tại của bạn.
```
wget https://wordpress.org/latest.zip
```
## 2.2 Tải về nhiều tập tin
Chúng ta cũng có thể sử dụng wget và tải xuống nhiều tệp cùng một lúc. Để làm điều đó, chúng ta sẽ cần tạo một file text chứa URL các file cần tải xuống.
```
# 1. Tạo file example.txt chứa các URL như sau
https://wordpress.org/latest.zip
https://downloads.joomla.org/cms/joomla3/3-8-5/Joomla_3-8-5-Stable-Full_Package.zip
https://ftp.drupal.org/files/projects/drupal-8.4.5.zip

# 2. Sử dụng câu lệnh sau để tải các file trong file example
wget -i example.txt
```

## 2.3 Tải tệp và lưu với một tên khác
```
wget -O wp-file.zip https://wordpress.org/latest.zip
```
Ở đây file **latest.zip** sẽ được tải xuống và lưu bằng file có tên **wp-file.zip**

## 2.4 Tải tệp và lưu vào một nơi được chỉ định
```
wget -P tailieu/luutru/ https://wordpress.org/latest.zip
```
File **latest.zip** sẽ được tải xuống và lưu trữ ở thư mục **tailieu/luutru/**

## 2.5 Giới hạn tốc độ tải xuống
Với wget, bạn cũng có thể giới hạn tốc độ tải xuống bằng tham số `–limit-rate`. Điều này rất hữu ích khi bạn tải các tệp lớn và sẽ ngăn không cho sử dụng toàn bộ băng thông của bạn. Lệnh wget này sẽ đặt giới hạn tải là 500KB:
```
wget –limit-rate=500k https://wordpress.org/latest.zip
```

## 2.6 Đặt số lần thử lại khi tải file thất bại
Một số sự cố kết nối Internet có thể khiến quá trình tải xuống của bạn bị gián đoạn. Để giải quyết vấn đề này, chúng ta có thể tăng số các lần thử lại bằng cách sử dụng tham số `-tries`:
```
wget -tries=100 https://wordpress.org/latest.zip
```
Câu lệnh trên sẽ **thử lại 100 lần** nếu xảy ra lỗi khi tải file.

## 2.7 Tải file ở chế độ background
Đối với các tệp cực lớn, bạn có thể tận dụng tham số **-b**. Nó sẽ tải nội dung của bạn dưới nền.
```
wget -b http://example.com/testing.zip
```
Một file `wget-log` sẽ xuất hiện trong thư mục làm việc của bạn, có thể được sử dụng để kiểm tra tiến trình và trạng thái tải xuống của bạn. Lệnh này cũng sẽ thực hiện in những dòng cuối của file `wget-log` đó:
```
tail -f wget-log
```

## 2.8 Tải file theo giao thức FTP
Lệnh này cũng có thể sử dụng được với giao thức FTP. Bạn chỉ cần xác định tên người dùng và mật khẩu như trong lệnh wget sau:
```
wget –ftp-user=USERNAME –ftp-password=YOUR_PASSWORD ftp://example.com/something.zip
```

## 2.9 Tiếp tục tải khi bị gián đoạn (resume download)
Quá trình tải xuống của bạn có thể bị gián đoạn nếu bạn mất kết nối internet hoặc bị mất điện. Điều này là khá phổ biến xảy ra khi tải xuống các tập tin lớn. Thay vì bắt đầu lại, bạn có thể tiếp tục tải xuống bằng cách sử dụng câu lệnh sau:
```
wget -c https://example/file-sieu-to-khong-lo.zip
```
Nếu bạn không thêm **tham số -c** vào câu lệnh trên, tệp mới sẽ tự thêm .1 vào cuối vì nó đã tồn tại.

# 3. Các lệnh wget nâng cao
## 3.1 Truy xuất toàn bộ trang web
Chúng ta cũng có thể sử dụng lệnh wget để tải xuống nội dung của toàn bộ trang web. Điều này sẽ cho phép bạn xem nó cục bộ mà không cần kết nối internet. Ví dụ:
```
wget –mirror –convert-links –page-requisites –no-parent -P documents/websites/ https://example.com
```
Các thành phần của lệnh trên:
- **–mirror:** Nó làm cho việc tải xuống của bạn thực hiện đệ quy.
- **–convert-links:** Tất cả các liên kết sẽ được chuyển đổi để thích hợp cho việc sử dụng ngoại tuyến .
- **–page-requisites:** bao gồm tất cả các tệp cần thiết như CSS, JS và hình ảnh.
- **–no-parent:** Nó đảm bảo rằng các thư mục trên hệ thống phân cấp không được truy xuất.
- **-P documents/websites/:** Điều này đảm bảo rằng tất cả nội dung đi đến thư mục được chỉ định của chúng ta.

Khi quá trình kết thúc, bạn sẽ có thể mở trang web đã tải xuống cục bộ và tìm tất cả các tệp trong thư mục documents/websites/

## 3.2 Xác định vị trí các liên kết bị hỏng
Hãy để thử một cái gì đó nâng cao hơn. Chúng ta có thể sử dụng lệnh wget để xác định tất cả các URL bị hỏng hiển thị lỗi 404 trên một trang web cụ thể. Bắt đầu bằng cách thực hiện như sau:
```
wget -o wget-log -r -l 5 –spider http://example.com
```
- **-o:** Tập hợp output thành một tập tin để sử dụng sau.
- **-l:** Chỉ định mức đệ quy.
- **-r:** Thực hiện đệ quy.
- **–spider:** Đặt wget vào chế độ spider.

Bây giờ chúng ta có thể kiểm tra tệp wget-log để tìm danh sách các liên kết bị hỏng. Đây là lệnh để thực hiện việc đó:
```
grep -B 2 '404' wget-log | grep "http" | cut -d " " -f 4 | sort -u
```

## 3.3 Tải các tệp được đánh số
Nếu bạn có tệp hoặc hình ảnh được đánh số trong một danh sách nhất định, bạn có thể dễ dàng tải xuống tất cả chúng với cú pháp sau:
```
wget http://example.com/images/{1..50}.jpg
```

# 4. Tải file từ Google Drive dùng wget
Trước hết, bạn cần biết rằng, Google Drive phân biệt 2 loại file là file dung lượng nhỏ và file dung lượng lớn. Các file có dung lượng dưới 100MB được gọi là nhỏ, còn trên 100MB thì là dung lượng lớn. Cách tải bằng lệnh `wget` cũng khác nhau đối với 2 trường hợp này.

Các bước thực hiện như sau:
1. Kiểm tra file trên Google Drive, đảm bảo file đã được share (trường hợp này là share `anyone`)
2. Lấy đường link file trên Google Drive, đường dẫn file trên Google Drive có có cấu trúc như sau:
```
https://drive.google.com/file/d/1jB7qjeIsCTkviKbnUxxxxx12E8aMHb_S0a/view?usp=sharing
```
Trong đó, đoạn `1jB7qjeIsCTkviKbnUflF12E8aMHb_S0a` chính là ID của file được lưu trên Google Drive.

Thực hiện tải file dùng wget
- Tải file dung lượng nhỏ
```
wget --no-check-certificate 'https://docs.google.com/uc?export=download&id=FILEID' -O FILENAME
```
- Tải file dung lượng lớn
```
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=FILEID' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=FILEID" -O FILENAME && rm -rf /tmp/cookies.txt
```
Trong đó `FILEID` là đoạn ID của file ở trên còn `FILENAME` là tên file bạn muốn lưu trên máy.

**Lưu ý:** Lệnh tải trên file dung lượng lớn có thể áp dụng được với cả file có dung lượng nhỏ. Nhưng lệnh với file dung lượng nhỏ không áp dụng được với file dung lượng lớn
# 5. Tham khảo
1. [https://linuxteamvietnam.us/wget-trong-linux-va-cach-su-dung/](https://linuxteamvietnam.us/wget-trong-linux-va-cach-su-dung/)
2. [https://raspberrypi.vn/su-dung-wget-de-tai-file-tu-google-drive-13020.pi](https://raspberrypi.vn/su-dung-wget-de-tai-file-tu-google-drive-13020.pi)