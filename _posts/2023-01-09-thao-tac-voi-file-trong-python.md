---
layout: post
author: d12life
title: Bài 10 - Thao tác file trong Python
---
Thao tác với file và folder là một thao tác quan trọng trong bất kỳ ngôn ngữ lập trình nào. Thao tác với file và folder có thể chia làm 2 loại: Thao tác không tác động đến nội dung file và thao tác tác động đến nội dung file. Trong bài viết này với thao tác không tác động đến nội dung file chúng ta sẽ xem xét 3 module là `os`, `shutil` và `glob` trong khi đó đối với thao tác tác động đến nội dung file chúng ta sẽ xem xét cách thức Python open file, thao tác và close file.

Trước khi thao tác file chúng ta có thể kiểm tra sự tồn tại của file/folder sử dụng các phương thức sau:
- **os.path.exists()**: Kiểm tra tồn tại của đường dẫn trong python
- **os.path.isfile()**: Kiểm tra tồn tại của file trong python
- **os.path.isdir()**: Kiểm tra tồn tại của thư mục trong python
- **Path.exists()**: Kiểm tra tồn tại của file và thư mục trong python

# 1. Thao tác không tác động đến nội dung file
Các thao tác không tác động đến nội dung file có thể kể đến như di chuyển giữa các thư mục, lấy ra danh sách, đổi tên, xóa file, ... Các thao tác này sẽ được xem xét qua 3 module như sau:

## 1.1 Module os
Có khá nhiều các phương thức trong module os, tuy nhiên trong thực tế chúng ta không cần nhớ hết tất cả các hàm, phương thức này. Ở đây chúng ta sẽ chỉ giới thiệu một vài phương thức chính.

### os.getcwd():
Hàm **getcwd()** trả về thư mục làm việc hiện tại của một tiến trình.

### os.listdir()
Phương thức này sẽ liệt kê tất cả các tệp, thư mục của đường dẫn được truyền vào

### os.walk()
Phương thức này sẽ duyệt qua hệ thống cây thư mục và trả về thông tin cây thư mục được bắt đầu từ đường dẫn được truyền vào bằng cách di di chuyển trên cây thư mục từ trên xuống hoặc từ dưới lên (dựa vào tham số topdown). Phương thức trả về một bộ gồm 3 thông tin sau (root, dirs, files).
- **root:** Chỉ: in ra các thư mục từ những gì bạn đã chỉ định.
- **dirs:** in ra các thư mục con từ root.
- **files:** in ra tất cả các tập tin từ thư mục gốc và thư mục.

Mặc định tham số topdown = True (chúng ta có thể bỏ qua hoặc gán tường minh topdown=True). Để duyệt cây thư mục từ dưới lên chúng ta sẽ set tham số topdown=False.

Ví dụ
```
import os

for (root,dirs,files) in os.walk('F:\\code', topdown=True):
    print(root) # Thư mục cần duyệt
    print(dirs) # list các thư mục con
    print(files) # list các file
    print('--------------------------------')
```
Kết quả
```
F:\code 
['test'] 
['example1.py', 'example2.txt'] 
--------------------------------
F:\code\test
[]
['example3.txt']
--------------------------------
```

### os.chdir()
Phương thức để thay đổi thư mục làm việc hiện tại

### Tạo thư mục/file bằng os.mkdir() và os.makdedirs()
Phương thức os.mkdir() cho phép chúng ta tạo thư mục/file ở đường dẫn được truyền. Sự khác biệt giữa mkdir() và makedirs() như sau
- os.makedirs('dirA/dirB') sẽ tạo cả thư mục A và thư mục B nếu thư mục A chưa tồn tại
- mkdir('dirA/dirB') sẽ tạo thư mục B nếu thư mục A đã tồn tại, nếu thư mục A chưa tồn tại phương thức này sẽ báo lỗi.

### os.rename()
Phương thức cho phép đổi tên file/thư mục.

### os.remove("my_file_path")
Xóa file ở đường dẫn được truyền vào.

Ngoài os.remove chúng ta cũng có thể sử dụng:
- **os.rmdir():** removes an empty directory.
- **shutil.rmtree():** deletes a directory and all its contents.
- **pathlib.Path.unlink():** removes the file or symbolic link.
- **pathlib.Path.rmdir():** removes the empty directory.

### os.path.join()
Module os.path chứa khá nhiều phương thức hữu ích cho các thao tác phổ biến để quản lý thư mục và file. Bạn có thể sử dụng nó để tìm thông tin về tên thư mục, các phần của tên thư mục, kiểm tra xem một tập tin hoặc thư mục tồn tại hay không ...

os.path.join() cho phép bạn có thể nối các đường dẫn với nhau theo để tạo nên 1 đường dẫn hoàn chỉnh và phù hợp nhất. Thay vì phải đau đầu sửa code để tạo đường dẫn theo từng hệ điều hành khác nhau, phương thức này sẽ giúp bạn tạo ra đường dẫn phù hợp nhất.

Lấy ví dụ, khi bạn làm việc hoặc chạy chương trình trên môi trường Unix hoặc MacOS, đường dẫn do os.path.join() tạo ra sẽ có dạng "duong_dan/den/file_hoac_folder", trong khi đó trên Windows thì đường dẫn sẽ là "duong_dan\den\file_hoac_folder". Hoặc khi bạn ghép nối 2 string: "duong_dan/" và "den/file_hoac_folder" thì kết quả sẽ là: "duong_dan//den/file_hoac_folder", trong khi sử dụng os.path.join() ta sẽ được "duong_dan/den/file_hoac_folder" một cách nhanh chóng.

## 1.2 Module shutil
Như đã nói ở trên, `shutil` chứa các hàm đặc trưng Python, cho phép người dùng thực hiện nhiều thao tác phức tạp hơn so với os. Các hàm của `shutil` thường gọi lại nhiều hàm của os.

### shutil.copy2("source_file", "destination")
Di chuyển file từ thư mục này sang thư mục khác.

Tại sao lại là copy2? Thực ra chúng ta có nhiều hàm copy khác với những mục đích khác nhau, copy2 cho phép copy cả các thông tin về metadata, permissions. Ngoài ra, đối số destination trong copy2 có thể là đường dẫn tới thư mục.
```
import shutil
shutil.copy2('/src/dir/file.ext', '/dst/dir/newname.ext')       # complete target filename given
shutil.copy2('/src/file.ext', '/dst/dir')                       # target filename is /dst/dir/file.ext
```

### shutil.move("source_file", "destination")
Di chuyển file từ thư mục này sang thư mục khác. Chúng ta cũng có thể dùng `os.rename` để có kết quả tương tự.
```
import os
import shutil

os.rename("path/to/current/file.foo", "path/to/new/destination/for/file.foo")
shutil.move("path/to/current/file.foo", "path/to/new/destination/for/file.foo")
```

Lưu ý rằng trong cả hai trường hợp, thư mục chứa file mới phải tồn tại sẵn, ngoài ra thì trên môi trường Windows, trong cùng một thư mục thì không được có file và thư mục con trùng tên nhau. Bạn cũng phải chú ý tên của file (file.foo) trong cả đối số nguồn và đích nếu không tập tin sẽ bị đổi tên 
trong khi di chuyển.

Thường thì `shutil.move` sẽ gọi lại `os.rename` trong hầu hết các trường hợp, tuy nhiên nếu đường dẫn đích nằm trên một đĩa khác với nguồn thì hàm này sẽ không sử dụng `os.rename` mà sẽ sao chép file trước bằng `shutil.copy2` sau đó xóa file nguồn. Nguyên nhân là os.rename sẽ chỉ làm việc khi đường dẫn nguồn và đường dẫn đích nằm trên cùng một ổ đĩa.

## 1.3 Lấy danh sách tên file và thư mục theo điều kiện trong python | glob.glob()
Để lấy danh sách tên file và thư mục phù hợp với điều kiện chỉ định, chúng ta sử dụng hàm glob.blog() với cú pháp sau đây:
```
glob.glob(pattern, *, recursive=False)
```
Trong đó:
- `pattern` là định dạng đường dẫn của file hoặc thư mục cần lấy.
- `recursive` chỉ định có sử dụng đệ quy hay không. Nếu recursive=True, chúng ta có thể lấy danh sách đệ quy tất cả file hay thư mục, bao gồm cả trong các thư mục con từ thư mục chỉ định.

Hàm sẽ trả về một list chứa tên của tất cả file và thư mục trong thư mục chỉ định mà có đường dẫn phù hợp với định dạng trong `pattern`.

Khi định dạng `pattern`, chúng ta có thể sử dụng kèm các ký tự đặc biệt sau đây để chỉ định điều kiện của đường dẫn
| Ký tự     | Ý nghĩa                     | Ví dụ                |
| ----------| ----------------------------| ---------------------|
| *         | Một chuỗi ký tự bất kỳ      | glob.glob(“*.txt”)   |
| ?         | Một ký tự đơn bất kỳ        | glob.glob(“./?”)     |
| []        | Một ký tự đơn trong phạm vi | glob.glob(“./[0-9]”) |


### Lấy danh sách tên file và thư mục khớp với một chuỗi ký tự bất kỳ | `*`
Ký tự `*` biểu thị điều kiện đường dẫn cần khớp với một chuỗi ký tự bất kỳ.
Ví dụ khi chỉ định `*.txt` , kết quả trả về sẽ là danh sách tên các file hoặc thư mục khớp với định dạng `một chuỗi ký tự bất kỳ` + `.txt`. Ví dụ như `user.txt` hoặc `address.txt`.

### Lấy danh sách tên file và thư mục khớp với một ký tự đơn bất kỳ | `?`
Ký tự `?` biểu thị điều kiện đường dẫn cần khớp với một ký tự đơn bất kỳ.
Ví dụ khi chỉ định `?.txt` , kết quả trả về sẽ là danh sách tên các file hoặc thư mục khớp với định dạng `một ký tự bất kỳ` + `.txt`. Ví dụ như `a.txt` hoặc `b.txt`.

### Lấy danh sách tên file và thư mục khớp một ký tự đơn trong phạm vi | `[]`
Ký tự `[]` viểu thị điều kiện đường dẫn cần khớp với một ký tự bất kỳ nằm giữa cặp dấu `[]`.
Ví dụ khi chỉ định `123[45].txt` , kết quả trả về sẽ là danh sách tên các file hoặc thư mục khớp với định dạng `123` + `4` hoặc `5`. Ví dụ như `1234.txt` hoặc `1235.txt`.

Chúng ta cũng có thể dùng cách viết biểu thị phạm vi bằng cách dùng dấu `-`, ví dụ như `[1-3]` để biểu thị `[123]`, hoặc `[a-f]` để biểu thị `[abcdef]`.

### Sử dụng ký tự đặc biệt `*` và `?` như một ký tự bình thường
Trong trường hợp bạn muốn dùng các ký tự đặc biệt `*` và `?` như một ký tự bình thường khi chỉ định điều kiện, hãy đặt chúng giữa cặp dấu `[]`, ví dụ như `[*]` và `[?]`.

Trong phần tiếp theo chúng ta sẽ dùng cây thư mục như sau để xét các trường hợp duyệt đệ quy:
```
data/
|-user
|  |-dir1
|  |-dir2
|  |  |-name.txt
|  |-pass.txt
|  |-direct.txt
|  |-user.txt 
|-client
|-move.py
```

## 1.4 Lấy danh sách đệ quy tên file và thư mục theo điều kiện trong python | recursive = True
Khi sử dụng hàm glob.glob() để lấy danh sách file và thư mục theo điều kiện trong python, nếu chúng ta chỉ định giá trị đối số `recursive = True`, một danh sách đệ quy bao gồm cả các file và thư mục chứa trong thư mục con cũng sẽ được lấy ra.

Và nếu chỉ định `pattern` của bằng ký tự đặc biệt `*`, chúng ta có thể chỉ định điều kiện để lấy file và thư mục ra.

Ví dụ, chúng ta dùng `*` để biểu thị khớp với bất kỳ tên thư mục nào cùng cấp, và dùng ** để biểu thị khớp với bất kỳ tên thư mục trung gian, như ví dụ sau:
```
print(glob.glob('data/user/*/*.text')) #Output: ['ata/user/name.text']

print(glob.glob('data/**/*.text', recursive=True)) Output: # ['data/user/user.txt', 'data/user/direct.txt', 'data/user/pass.txt', 'data/user/dir2/name.text']
```

Ngoài ra, chúng ta sử dụng cách viết `tên thư mục` + `/**` để lấy toàn bộ file và thư mục có trong thư mục được chỉ định như sau:
```
print(glob.glob('user/**', recursive=True)) #Output: ['./user/', './user/dir1', './user/dir2','./user/dir2/name.txt']
```

## 1.5 Lấy danh sách tên file và thư mục theo điều kiện trong python | Path.glob()
Chúng ta cũng có thể sử dụng phương thức Path.glob() tích hợp trong module pathlib để lấy danh sách tên file và thư mục theo điều kiện trong python, với cú pháp sau đây:
```
Path.glob(pattern)
```

Trong đó `Path` là một instance được tạo ra từ class pathlib.Path() chứa thông tin đường dẫn của thư mục gốc.

`Pattern` cũng giống như với hàm lob.glob(), là định dạng đường dẫn của file hoặc thư mục cần lấy, gồm `*`, `?` và `[]`. Cách sử dụng các ký tự đặc biệt này tương tự như chúng ta đã xem xét ở phần trên.

Chúng ta lần lượt chỉ định các pattern để lấy danh sách tên các file và thư mục phù hợp với điều kiện như sau:
```
import pathlib

p = pathlib.Path('./data')
for name in p.glob('[a-d]*.txt'):
  print(name)
Output: Không có output do ko có file .txt thỏa mãn pattern

for name in p.glob('./user/????.txt'):
    print(name)

Output: # pass.txt, # user.txt
```

## 1.6 Lấy danh sách đệ quy tên file và thư mục theo điều kiện trong python | Path.glob()
Tương tự với hàm glob.glob(), chúng ta cũng có thể sử dụng phương thức path.glob() để lấy danh sách đệ quy tên file và thư mục theo điều kiện trong python.
Có một điểm khác là hàm glob.glob() cần chỉ định `recursive=True` làm đối số thì mới có thể xử lý đệ quy, trong khi với phương thức path.glob() thì về mặc định xử lý đã là xử lý đệ quy rồi.
Chúng ta sẽ kết hợp cách viết ``**`` khi chỉ định pattern của đường dẫn như sau:
```
import pathlib

p = pathlib.Path('./user')
for name in p.glob('**/*.txt'):
  print(name)

Output: #./user/pass.txt, #./user/directdirec.txt, #./user/user.txt, #./user/dir2/name.txt
```

# 2. Thao tác có tác động đến nội dung file (đọc/ghi file)
Trong Python có 2 loại file:

Text file
- Được cấu trúc như một dãy các dòng, mỗi dòng bao gồm một dãy các kí tự và một dòng tối thiểu là một kí tự dù cho dòng đó là dòng trống.
- Các dòng trong text file được ngăn cách bởi một kí tự newline và mặc định trong Python chính là kí tự `escape sequence newline` **\n**.

Binary file
- Các file này chỉ có thể được xử lí bởi một ứng dụng biết và có thể hiểu được cấu trúc của file này.
- Và chúng ta ở đây với mức độ cơ bản chỉ xử lí text file.

## Mở file
```
open(file, mode='r', buffering=-1, encoding=None, errors=None, newline=None, closefd=True, opener=None)
```

Ở mức độ cơ bản chúng ta chỉ cần quan tâm đến  đối số
- file: Đường dẫn file chúng ta muốn thao tác
- mode: Các mode tác động đến file được mô tả như bảng bên dưới

mode |Mục đích truy cập              
-----|-------------------------------
r    |Mở để đọc, đây là mode mặc định. Con trỏ tệp trỏ vào đầu tệp.
r+   |Mở để đọc và ghi. Con trỏ tệp trỏ vào đầu tệp.
w    |Mở để ghi. Trước đó nó sẽ xóa hết nội dung file hiện có. Nếu file không tồn tại sẽ tạo mộ file với tên file là tên truyền vào.
w+   |Mở để ghi và đọc. Trước đó nó cũng xóa hết nội dung của file hiện có. Nếu file không tồn tại sẽ tạo mộ file với tên file là tên truyền vào.
a    |Mở để ghi theo kiểu nối thêm (append). Con trỏ tệp trỏ vào cuối tệp. Nếu file không tồn tại sẽ tạo mộ file với tên file là tên truyền vào.
a+   |Mở để ghi theo kiểu nối thêm (append) và đọc. Con trỏ tệp trỏ vào cuối tệp. Nếu file không tồn tại sẽ tạo mộ file với tên file là tên truyền vào.

## Đóng file
```
<File>.close()
```

Tại sao chúng ta nên đóng file sau khi hoàn tất công việc với file?
- Lãng phí tài nguyên, chưa được đóng sẽ chiếm dụng tài nguyên máy tính đặc biệt là các file có dung lượng lớn.
- Lock file, hệ điều hành sẽ không cho các chương trình khác có thể xử lý trên file để đảm bảo tính nhất quán của dữ liệu.

Khi chương trình thực hiện xong, tất cả các file đang mở sẽ được đóng lại. Tuy nhiên để giải phóng tài nguyên và không chiếm giữ quyền truy cập chúng ta nên đóng file ngày khi có thể.

## Đọc file
### Phương thức read
```
<File>.read(size=-1)
```

Trong đó: 
- `size` là số ký tự sẽ được đọc, nếu size=-1 hoặc không truyền vào thì phương thức sẽ đọc hết và đưa con trỏ xuống cuối file.
- Phương thức trả về nội dung dạng chuỗi các ký tự, nếu file trống hoặc con trỏ đã ở cuối file giá trị trả về sẽ là một chuỗi rỗng.

### Phương thức readline
```
<File>.readline(size=-1)
```
Trong đó: Tham số size được áp dụng cho dòng thay vì cho toàn bộ file như phương thức read(). Size là số ký tự muốn đọc trên dòng, nếu không truyền hoặc size=-1 thì đọc toàn bộ dòng.

Một số lưu ý với phương thức readlin() như sau:
- Phương thức readline chỉ đọc từng dòng một (đọc tới khi nào gặp newline hoặc hết file thì ngừng).
- Con trỏ file cũng sẽ đi từ dòng này qua dòng khác.
- Kết quả đọc được trả về dưới dạng một chuỗi.
- Nếu không đọc được gì, phương thức sẽ trả về một chuỗi có độ dài bằng 0.

### Phương thức readlines
```
<File>.readlines(hint=-1)
```
Trong đó: `hint` là số byte gợi ý trả về. Nếu số byte được trả về vượt quá số gợi ý, sẽ không có dòng nào được trả về nữa. Giá trị mặc định là -1, có nghĩa là tất cả các dòng sẽ được trả về.

Phương thức này sẽ đọc toàn bộ file, sau đó cho chúng vào một list. Với các phần tử trong list là mỗi dòng của file.

Con trỏ file sẽ được đưa  tới cuối file. Khi đó, nếu bạn tiếp tục dùng readlines. Bạn sẽ nhận được một list rỗng.

### Đọc file bằng constructor nhận iterable
File object nhận được từ hàm open cũng là một **iterable**. Do đó ta có thể sử dụng constructor list.
```
>>> fobj = open('kteam.txt')
>>> list_content = list(fobj)
>>> list_content
['How Kteam\n', 'Free Education\n', '\n', 'Share to better\n', '\n', "print('hello world!')\n"]
>>> fobj.close()
```
Và cũng có thể là Tuple.
```
>>> fobj = open('kteam.txt')
>>> tup_content = tuple(fobj)
>>> tup_content
('How Kteam\n', 'Free Education\n', '\n', 'Share to better\n', '\n', "print('hello world!')\n")
>>> fobj.close()
```
Các constructor này cũng sẽ đưa con trỏ file xuống cuối file.

## Ghi file trong Python
### Phương thức write
```
<File>.write(text)
```
Phương thức này ghi nội dung (`text`) vào file và trả về số kí tự đã được ghi vào. Mỗi lần sử dụng write con trỏ file sẽ được đặt ngay sau kí tự cuối cùng được ghi.

Lưu ý: Khi sử dụng `open()` với mode `w` dữ liệu trong file sẽ bị ghi đè, nếu muốn tiếp tục ghi vào file sẵn có chúng ta sẽ sử dụng mode `a`.

## Kiểm soát con trỏ file
### Phương thức seek
```
<File>.seek(offset, whence=0)
```
Phương thức này giúp ta di chuyển con trỏ từ vị trí đầu file qua offset kí tự (offset phải là một số tự nhiên). Nhờ phương thức này, ta có thể ghi nội dung từ bất cứ đâu trong file. Và có thể đọc lại file sau khi ta đưa con trỏ xuống cuối file.

**Lưu ý**: Với Python 3.X, phương thức áp dụng cho text file khi `whence = 0`, áp dụng cho binary file khi `whence = 1` hoặc `whence = 2`. Với Python 2.X chúng ta không cần quan tâm đến vấn đề này.
```
>>> fobj = open('kteam.txt')
>>> fobj.read()
"How Kteam\nFree Education\n\nShare to better\n\nprint('hello world!')\n"
>>> fobj.read()
''
>>> fobj.seek(0)
0
>>> fobj.read()
"How Kteam\nFree Education\n\nShare to better\n\nprint('hello world!')\n"
>>> fobj.seek(10)
10
>>> fobj.read()
"\nFree Education\n\nShare to better\n\nprint('hello world!')\n"
>>> fobj.close()
```

## Câu lệnh with
```
with expression [as variable]:
    with-block    
```
Câu lệnh này liên quan đến phương thức __enter__ và __exit__ của đối tượng. Do đó, ở đây chúng ta sẽ nói cơ bản khi sử dụng file.

Đặc điểm của câu lệnh with khi sử dụng với file là. Khi kết thúc with-block. File sẽ được đóng.
```
>>> with open('kteam.txt') as fobj:
...     data = fobj.read()
...
>>> data
"How Kteam\nFree Education\n\nShare to better\n\nprint('hello world!')\n"
>>> fobj.read() # không thể đọc file, vì file đã đóng
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: I/O operation on closed file.
```
Tất nhiên, có thể sử dụng câu lệnh with kết hợp với toán tử :=
```
>>> with (fi := open("kteam.txt", 'r')):
...   data = fi.read()
...
>>> data
"How Kteam\nFree Education\n\nShare to better\n\nprint('hello world!')\n"
```

# 3. Tham khảo
1. [https://blog.luyencode.net/module-os-trong-python/](https://blog.luyencode.net/module-os-trong-python/)
2. [https://cuccode.com/python_os_and_shutil.html](https://cuccode.com/python_os_and_shutil.html)
3. [https://laptrinhcanban.com/python/nhap-mon-lap-trinh-python/xu-ly-file-trong-python/lay-danh-sach-ten-file-va-thu-muc-theo-dieu-kien-trong-python/](https://laptrinhcanban.com/python/nhap-mon-lap-trinh-python/xu-ly-file-trong-python/lay-danh-sach-ten-file-va-thu-muc-theo-dieu-kien-trong-python/)
4. [https://howkteam.vn/course/lap-trinh-python-co-ban/xu-ly-file-trong-python-1570](https://howkteam.vn/course/lap-trinh-python-co-ban/xu-ly-file-trong-python-1570)