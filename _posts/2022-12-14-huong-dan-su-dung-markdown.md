---
layout: post
author: d12life
title: Bài 2 - Hướng dẫn sử dụng markdown
---

# Mở đầu
Markdown là ngôn ngữ đánh dấu văn bản được tạo ra bởi John Gruber, sử dụng cú pháp khá đơn giản và dễ hiểu, dễ nhớ. Nếu nắm vững các cú pháp của Markdown bạn có thể trình bày bài viết của mình một cách mạch lạc, ấn tượng mà không mất nhiều thời gian. Bài viết dưới đây sẽ hướng dẫn để bạn có thể hiểu và sử dụng được ngay những cú pháp đó.

# Nội dung
## Tiêu đề
Bạn có thể viết các lớp tiêu đề h1, h2, h3 cho đến h6 bằng cách thêm số lượng ký tự # tương ứng vào đầu dòng. Một ký tự # tương đương với h1, 2 ký tự # tương đương với h2 ...
```
# h1
## h2
### h3
#### h4
##### h5
###### h6
```

## Nhấn mạnh, highlight
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

# Link, image
## Link
Để chèn link vào bài viết, bạn dùng cú pháp sau
```
[title](http://~)
```

Ví dụ
```
[Markdown](http://https://vi.wikipedia.org/wiki/Markdown)
```
Kết quả: [Markdown]()

## Image
Cú pháp chèn hình ảnh như sau
```
![alt](http://~)
```

Ví dụ
```
![markdown](https://images.viblo.asia/518eea86-f0bd-45c9-bf38-d5cb119e947d.png)
```
![markdown](https://images.viblo.asia/518eea86-f0bd-45c9-bf38-d5cb119e947d.png)

# List
## List dạng gạch đầu dòng
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
## List dạng số
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

# Horizonal rules
Để có được horizonal rules bạn chỉ cần viết *** như sau
```
***
horizonal rules
```
Kết quả
***
horizonal rules

# Blockquotes

Cú pháp blockquotes là
```
> text
```
Kết quả
> text

# Escape markdown
Đôi khi trong khi viết bài bạn sẽ sử dụng những kí kiệu trùng với cú pháp của markdown. Để phân biệt, bạn chỉ cần thêm dấu \ trước những kí hiệu đó là được.

Ví dụ nếu bạn viết
```
\*text*
```
Kết quả sẽ là \*text* không phải *text* (in nghiêng)

# Viblo advanced Markdown Embedment

**Cách 1**: Dùng cú pháp dưới đây để chèn link video từ tất cả các nguồn:
```
{@embed: URL}
```
Ví dụ: {@embed: https://www.youtube.com/watch?v=HndN6P9ke6U}

**Cách 2**: Hiện tại Viblo hỗ trợ chèn link từ **Youtube, Vimeo, Slideshare, Codepen, Gist, JSFiddle** và **Google Slide**. Cú pháp như dưới đây:
## Youtube
```
{@youtube: Youtube ID or URL}
```
Ví dụ:
```
{@youtube: https://www.youtube.com/watch?v=HndN6P9ke6U}
```
{@youtube: https://www.youtube.com/watch?v=HndN6P9ke6U}

## Vimeo
```
{@vimeo: Vimeo ID or URL}
```
Ví dụ:
```
{@vimeo: https://vimeo.com/62604492}
```
{@vimeo: https://vimeo.com/62604492}

## Slideshare
```
{@slideshare: Slideshare ID or URL}
```
Ví dụ:
```
{@slideshare: http://www.slideshare.net/asanzdiego/markdown-slides-en}
```
{@slideshare: http://www.slideshare.net/asanzdiego/markdown-slides-en}

## Codepen
```
{@codepen: Codepen ID or URL}
```
Ví dụ:
```
{@codepen: https://codepen.io/nickmoreton/pen/gbyygq}
```
{@codepen: https://codepen.io/nickmoreton/pen/gbyygq}

## Gist
```
{@gist: Gist ID or URL}
```
Ví dụ
```
{@gist: https://gist.github.com/JeffreyWay/207e3bfdb5cafff050a1d75dbf755a5c}
```
{@gist: https://gist.github.com/JeffreyWay/207e3bfdb5cafff050a1d75dbf755a5c}

## JSFiddle
```
{@jsfiddle: JSFiddle URL}
```
Ví dụ:
```
{@jsfiddle: http://jsfiddle.net/kizu/zfUyN/}
```
{@jsfiddle: http://jsfiddle.net/kizu/zfUyN/}

## Google slide
Đối với tài liệu bạn muốn chia sẻ từ Google slide thì bạn cần phải public tài liệu đó để mọi người có thể xem được, rồi dùng link tài liệu đã được public với cú pháp sau:
```
{@googleslide: document_link}
```
Ví dụ
```
{@googleslide: https://docs.google.com/presentation/d/1nJ65LUlu9k_tfuQJ4jq4z-qmqOQZ0DjKKw8wn5qnnFA/edit#slide=id.p}
```
{@googleslide: https://docs.google.com/presentation/d/1nJ65LUlu9k_tfuQJ4jq4z-qmqOQZ0DjKKw8wn5qnnFA/edit#slide=id.p}

Đối với những người mới sử dụng thì hẳn là chưa thể nhớ hết được những cú pháp của markdown, nhưng bạn hãy yên tâm vì bạn luôn có thể xem chỉ dẫn cú pháp markdown bằng cách click vào biểu tưởng dấu hỏi được đính ở phía trên của editor.

# Công thức toán học
Bên cạnh các cú pháp Markdown phổ biến, Viblo còn hỗ trợ viết các công thức toán học theo cú pháp của ***TeX***.