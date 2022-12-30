---
layout: post
author: d12life
title: Bài 9 - Một số kiểu dữ liệu trong Python
---
# 1. Cách sử dụng một số hàm trong python
## 1.1 Hàm zip()
**Hàm zip() trong Python** trả về một đối tượng zip, là một iterator dạng danh sách các tuple kết hợp các phần tử từ các iterator (được tạo thành từ các iterable) khác.

### Cú pháp hàm zip() trong Python
```
zip(*iterable)
```
(Iterable là một đối tượng sau khi sử dụng các phương thức sẽ trả về một iterator, ví dụ như Chuỗi, List, Tuple).

#### Tham số của hàm zip()
Hàm zip() trong Python có tham số:
- *iterable*: các iterable được tích hợp sẵn (như list, string, dict) hoặc iterable do người dùng khai báo (được tạo thành từ phương thức `__iter__`)

### Giá trị trả về từ zip()
Hàm zip () trả về một iterator của các bộ dữ liệu tuple dựa trên iterable object.
- Nếu không có tham số nào được truyền, zip() trả về một iterator rỗng.
- Nếu tham số được truyền chỉ có duy nhất một iterable, zip() trả về tuple có 1 phần tử.
- Nếu tham số được truyền có nhiều iterable và độ dài của các iterable không bằng nhau, zip sẽ tạo các tuple có độ dài bằng với số iterable nhỏ nhất.

### Cách sử dụng zip()
#### Ví dụ 1: Cách zip() hoạt động trong Python
```
numberList = [1, 2, 3]
strList = ['one', 'two', 'three']
```
```
# Không truyền iterable
result = zip()
# Chuyển đổi iterator thành list
resultList = list(result)
print(resultList)
```
```
[]
```
```
# Truyền 2 iterator
result = zip(numberList, strList)
# Chuyển đổi iterator thành set
resultSet = set(result)
print(resultSet)
```
```
{(2, 'two'), (3, 'three'), (1, 'one')}
```

#### Ví dụ 2: Các iterator có số phần tử khác nhau
```
numbersList = [1, 2, 3]
strList = ['one', 'two']
numbersTuple = ('ONE', 'TWO', 'THREE', 'FOUR')
```
```
result = zip(numbersList, numbersTuple)
# Chuyển đổi thành set
resultSet = set(result)
print(resultSet)
```
```
{(2, 'TWO'), (3, 'THREE'), (1, 'ONE')}
```
```
result = zip(numbersList, strList, numbersTuple)
# Chuyển đổi thành set
resultSet = set(result)
print(resultSet)
```
```
{(2, 'two', 'TWO'), (1, 'one', 'ONE')}
```

Toán tử * có thể được sử dụng cùng với zip() để giải nén danh sách.

#### Ví dụ 3: Giải nén giá trị bằng cách sử dụng zip()
```
coordinate = ['x', 'y', 'z']
value = [3, 4, 5, 0, 9]
result = zip(coordinate, value)
resultList = list(result)
print(resultList)
```
```
[('x', 3), ('y', 4), ('z', 5)]
```
```
c, v = zip(*resultList)
print('c =', c)
print('v =', v)
```
```
c = ('x', 'y', 'z')
v = (3, 4, 5)
```

## 2 Lấy danh sách tên file và thư mục theo điều kiện trong python
Để lấy danh sách tên file và thư mục phù hợp với điều kiện chỉ định, chúng ta sử dụng hàm glob.blob() với cú pháp sau đây:
```
glob.glob(pattern, *, recursive=False)
```
Trong đó
- `pattern` là định dạng đường dẫn của file hoặc thư mục cần lấy.
- `recursive` chỉ định có sử dụng đệ quy hay không. Nếu `recursive=True`, chúng ta có thể lấy danh sách đệ quy tất cả file hay thư mục, bao gồm cả trong các thư mục con từ thư mục chỉ định.



#  Tham khảo
1. [https://www.vithon.org/2009/06/duyet-qua-cac-file-trong-mot-thu-muc.html](https://www.vithon.org/2009/06/duyet-qua-cac-file-trong-mot-thu-muc.html)
2. [https://stackoverflow.com/questions/66238786/splitting-image-based-dataset-for-yolov3](https://stackoverflow.com/questions/66238786/splitting-image-based-dataset-for-yolov3)
3. [https://quantrimang.com/hoc/gioi-thieu-qua-ve-chuoi-so-list-trong-python-140881](https://quantrimang.com/hoc/gioi-thieu-qua-ve-chuoi-so-list-trong-python-140881)