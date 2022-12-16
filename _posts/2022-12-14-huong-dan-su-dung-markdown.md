---
layout: post
author: d12life
title: Bài 2 - Hướng dẫn sử dụng markdown
---

# 1. Mở đầu
Markdown là ngôn ngữ đánh dấu văn bản được tạo ra bởi John Gruber, sử dụng cú pháp khá đơn giản và dễ hiểu, dễ nhớ. Nếu nắm vững các cú pháp của Markdown bạn có thể trình bày bài viết của mình một cách mạch lạc, ấn tượng mà không mất nhiều thời gian. Bài viết dưới đây sẽ hướng dẫn để bạn có thể hiểu và sử dụng được ngay những cú pháp đó.

# 2. Nội dung
## 2.1. Tiêu đề
Bạn có thể viết các lớp tiêu đề h1, h2, h3 cho đến h6 bằng cách thêm số lượng ký tự # tương ứng vào đầu dòng. Một ký tự # tương đương với h1, 2 ký tự # tương đương với h2 ...
```
# h1
## h2
### h3
#### h4
##### h5
###### h6
```

## 2.2. Nhấn mạnh, highlight
Bạn có thể kẹp một từ ở đầu và cuối bằng 1 ký tự * để in nghiêng, 2 ký tự ** để bôi đậm, và 3 ký tự *** để ***vừa in nghiêng vừa bôi đậm***.
```
*in nghiêng*
**bôi đậm**
***vừa in nghiêng vừa bôi đậm***
```

 Để viết inline code, bạn dùng cú pháp

`inlide code`

Để highlight block code, bạn viết
```
php

echo ("highlight code");
```

## 2.3. Link, image
### 2.3.1 Link
Để chèn link vào bài viết, bạn dùng cú pháp sau
```
[title](http://~)
```

Ví dụ
```
[Markdown](http://https://vi.wikipedia.org/wiki/Markdown)
```
Kết quả: [Markdown]()

### 2.3.2. Image
Cú pháp chèn hình ảnh như sau
```
![alt](http://~)
```

Ví dụ
```
![markdown](https://images.viblo.asia/518eea86-f0bd-45c9-bf38-d5cb119e947d.png)
```
![markdown](https://images.viblo.asia/518eea86-f0bd-45c9-bf38-d5cb119e947d.png)

## 2.4. List
### 2.4.1. List dạng gạch đầu dòng
```
* item
```

Ví dụ
```
* item 1
* item 2
* item 3
```
Kết quả
* item 1
* item 2
* item 3
### 2.4.2. List dạng số
Ví dụ
```
1. item 1
2. item 2
3. item 3
```
Kết quả
1. item 1
2. item 2
3. item 3

## 2.5. Horizonal rules
Để có được horizonal rules bạn chỉ cần viết *** như sau
```
***
horizonal rules
```
Kết quả
***
horizonal rules

## 2.6. Blockquotes

Cú pháp blockquotes là
```
> text
```
Kết quả
> text

## 2.7. Escape markdown
Đôi khi trong khi viết bài bạn sẽ sử dụng những kí kiệu trùng với cú pháp của markdown. Để phân biệt, bạn chỉ cần thêm dấu \ trước những kí hiệu đó là được.

Ví dụ nếu bạn viết
```
\*text*
```
Kết quả sẽ là \*text* không phải *text* (in nghiêng)

## 2.8. Công thức toán học
Bên cạnh các cú pháp Markdown phổ biến, Viblo còn hỗ trợ viết các công thức toán học theo cú pháp của ***TeX***.