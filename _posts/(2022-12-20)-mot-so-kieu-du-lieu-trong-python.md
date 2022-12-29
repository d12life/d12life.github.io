---
layout: post
author: d12life
title: Bài 9 - Giới thiệu một số kiểu dữ liệu trong Python
---

Python là một trong số ngôn ngữ lập trình phổ biến nhất hiện nay với nhiều kiểu dữ liệu vô cùng đa dạng và phong phú. Trong bài viết này chúng ta chỉ đi sâu tìm hiểu một số kiểu dữ liệu cấp cao như List và Dictionary, các kiểu dữ liệu còn lại như int, float, Boolean sẽ không được xem xét trong phạm vi của bài viết này.

# 1. Danh sách (List)
Trong Python, list được biểu diễn bằng dãy các giá trị, được phân tách nhau bằng dấu phẩy, nằm trong dấu []. Các danh sách có thể chứa nhiều mục với kiểu khác nhau, nhưng thông thường là các mục có cùng kiểu. List cũng có thể là các danh sách lồng nhau
```
list1 = [] # list rỗng
list2 = [1, 2, 3] # list số nguyên
list3 = [1, "Hello", 3.4] # list với kiểu dữ liệu hỗn hợp
list4 = ["mouse", [8, 4, 6], ['a']] # list lồng nhau
```
## 1.1 Truy cập List
Để truy cập vào một phần tử của list ta sử dụng toán tử index []. Index bắt đầu từ 0, truy cập vào phần tử có index khác index của list sẽ làm phát sinh lỗi IndexError. Index phải là một số nguyên, không thể sử dụng float, hay kiểu dữ liệu khác, sẽ báo lỗi TypeError.
```
qtm_list = ['q','u','a','n','t','r','i','m','a','n','g','.','c','o','m']

# TypeError: list indices must be integers or slices, not float
qtm_list[2.0]
```

List lồng nhau sẽ được truy cập bằng index lồng nhau:
```
# List lồng nhau
ln_list = ["Happy", [1,3,5,9]]

# Index lồng nhau
print(ln_list[0][1]) # Output: a
print(ln_list[1][3]) # Output: 9
```

Python cũng cho phép lập chỉ mục âm cho các chuỗi, index âm dùng để đếm phần tử của chuỗi ngược từ cuối lên đầu. Index -1 là phần tử cuối cùng, -2 là phần tử thứ 2 từ cuối cùng lên.
```
qtm_list = ['q','u','a','n','t','r','i','m','a','n','g','.','c','o','m']

print(qtm_list[-1]) # Output: m
print(qtm_list[-9]) # Output: i
```

Đối với việc truy cập 1 dải của List, Python sử dụng toán tử slice (: dấu hai chấm). Toán tử slice trả về list mới chứa những phần tử được yêu cầu.
```
qtm_list = ['q','u','a','n','t','r','i','m','a','n','g','.','c','o','m']

print(qtm_list[1:5]) # Output: ['u', 'a', 'n', 't']
print(qtm_list[:-8]) # Output: ['q', 'u', 'a', 'n', 't', 'r', 'i']
print(qtm_list[9:]) # Output: ['n', 'g', '.', 'c', 'o', 'm']
```

Nếu thực hiện slice [:] thì hệ thống sẽ trả về một list mới là bản sao của list ban đầu:
```
qtm_list = ['q','u','a','n','t','r','i','m','a','n','g','.','c','o','m']

print(qtm_list[:]) # Output: Bản sao của qtm_list
```

# 1.2 Các thao tác trên List
Không giống như chuỗi, các phần tử bị gán cố định, list là kiểu dữ liệu có thể thay đổi.
```
>>> cubes = [1, 8, 27, 65, 125]
>>> cubes[3] = 64 # thay thế giá trị tại vị trí có index=3
>>> cubes
[1, 8, 27, 64, 125]
```

Thêm phần tử mới vào cuối list sử dụng `append()`
```
>>> cubes.append(216)
>>> cubes
[1, 8, 27, 64, 125, 216]
```

Việc gán một dải các phần tử (slice) cho list cũng có thể thực hiện được, gán dải cho list đôi khi làm thay đổi cả kích thước của list hoặc xóa nó hoàn toàn.
```
>>> letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g']
>>> letters
['a', 'b', 'c', 'd', 'e', 'f', 'g']
>>> # thay thế các giá trị có index=2,3,4 thành chữ in hoa
>>> letters[2:5] = ['C', 'D', 'E']
>>> letters
['a', 'b', 'C', 'D', 'E', 'f', 'g']
>>> # xóa các phần tử này sẽ làm kích thước của list thay đổi
>>> letters[2:5] = []
>>> letters
['a', 'b', 'f', 'g']
>>> # xóa list bằng cách thay tất cả các phần tử bằng một list rỗng
>>> letters[:] = []
>>> letters
[]
```

Chúng ta cũng có thể tạo ra list mới bằng cách gộp 2 List:
```
>>> squares = [1, 4, 9, 16, 25]
>>> squares + [36, 49, 64, 81, 100]
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

Để kiểm tra xem một phần tử đã có trong list hay chưa sử dụng keyword `in`. Nếu phần tử có tồn tại, trả về là True, ngược lại trả về False.
```
QTM = ['q','u','a','n','t','r','i','m','a','n','g','.','c','o','m']

print('q' in QTM) # Output: True
print('.' in QTM) # Output: True
print('z' in QTM) # Output: False
```

Duyệt qua các phần tử của list sử dụng `for`:
```
for ngon_ngu in ['Python','Java','C']:
    print("Tôi thích lập trình",ngon_ngu)

# Output:
Tôi thích lập trình Python
Tôi thích lập trình Java
Tôi thích lập trình C
```

Lấy ra kích thước list dùng hàm `len()`:
```
>>> letters = ['a', 'b', 'c', 'd']
>>> len(letters)
4
```

Xóa một hoặc nhiều phần tử khỏi list hoặc xóa hoàn toàn cả list sử dụng từ khóa `del`.
```
my_list = ['q','u','a','n','t','r','i','m','a','n','g','.','c','o','m']

del my_list[2] # xóa phần tử có index=2
print(my_list) # Output: ['q', 'u', 'n', 't', 'r', 'i', 'm', 'a', 'n', 'g', '.', 'c', 'o', 'm']

# xóa phần tử có index từ 1 đến 7 (ko bao gồm index=7)
del my_list[1:7]
print(my_list) # Output: ['q', 'a', 'n', 'g', '.', 'c', 'o', 'm']

# xóa toàn bộ list my_list
del my_list
print(my_list) # Error: NameError: name 'my_list' is not defined
```

Ngoài ra chúng ta cũng có thể sử dụng `remove()` để loại bỏ những phần tử đã cho hoặc `pop()` để loại bỏ phần tử tại một index nhất định. `pop()` loại bỏ và trả về phần tử cuối cùng nếu index không được chỉ định. Điều này giúp triển khai list dưới dạng stack (ngăn xếp) (cấu trúc dữ liệu first in last out - vào đầu tiên, ra cuối cùng).

Phương thức `clear()` cũng được dùng để làm rỗng một list (xóa tất cả các phần tử trong list).
```
my_list = ['q','u','a','n','t','r','i','m','a','n','g','.','c','o','m']
my_list.remove('.') # xóa phần tử '.' khỏi list
 print(my_list) # Output: ['q', 'u', 'a', 'n', 't', 'r', 'i', 'm', 'a', 'n', 'g', 'c', 'o', 'm']

print(my_list.pop(3)) # Output: n, phần tử ở index=3 bị xóa khỏi list
print(my_list) # Output: ['q', 'u', 'a', 't', 'r', 'i', 'm', 'a', 'n', 'g', 'c', 'o', 'm']

print(my_list.pop()) # Output: m, xóa phần tử và trả về phần tử cuối cùng của list
print(my_list) # Output: ['q', 'u', 'a', 't', 'r', 'i', 'm', 'a', 'n', 'g', 'c', 'o']

my_list.clear()
print(my_list) # Output: [] (list rỗng)
```

Cách cuối cùng để xóa các phần tử trong một list là gán một list rỗng cho các lát phần tử.
```
>>> my_list = ['q','u','a','n','t','r','i','m','a','n','g','.','c','o','m']
>>> my_list[11:15]=[]
>>> my_list
['q', 'u', 'a', 'n', 't', 'r', 'i', 'm', 'a', 'n', 'g']
```
## 1.3 Phương thức list trong Python
Những phương thức có sẵn cho list trong Python gồm:
- **append():** Thêm phần tử vào cuối list.
- **extend():** Thêm tất cả phần tử của list hiện tại vào list khác.
- **insert():** Chèn một phần tử vào index cho trước.
- **remove():** Xóa phần tử khỏi list.
- **pop():** Xóa và trả về phần tử tại index đã cho, nếu không chỉ định index thì xóa và trả về phần tử cuối cùng của list.
- **clear():** Xóa tất cả phần tử của list.
- **index():** Trả về index của phần tử phù hợp đầu tiên.
- **count():** Trả về số lượng phần tử đã đếm được trong list như một đối số.
- **sort():** Sắp xếp các phần tử trong list theo thứ tự tăng dần.
- **reverse():** Đảo ngược thứ tự các phần tử trong list.
- **copy():** Trả về bản sao của list.
```
QTM = [9,8,7,6,8,5,8]
print(QTM.index(7)) # Output: 2
print(QTM.count(8)) # Output: 3, có 3 số 8 trong list

QTM.sort() # sắp xếp list tăng dần
print(QTM) # Output: [5, 6, 7, 8, 8, 8, 9]

QTM.reverse() # đảo ngược list
print(QTM) # Output: [9, 8, 8, 8, 7, 6, 5]
```
```
QTM = ['q','u','a','n','t','r','i','m','a','n','g','.','c','o','m']
print(QTM.index('n')) # Output: 3
print(QTM.count('a')) # Output: 2, có 2 chữ a trong list

QTM.sort() # sắp xếp list theo thứ tự tăng
print(QTM) # Output: ['.', 'a', 'a', 'c', 'g', 'i', 'm', 'm', 'n', 'n', 'o', 'q', 'r', 't', 'u']

QTM.reverse() # đảo ngược list
print(QTM) # Output: ['u', 't', 'r', 'q', 'o', 'n', 'n', 'm', 'm', 'i', 'g', 'c', 'a', 'a', '.']
```

## 1.4 List comprehension: Cách tạo list mới ngắn gọn
List comprehension là một biểu thức đi kèm với lệnh for được đặt trong cặp dấu ngoặc vuông [].

Đoạn code sau
```
cub3 = [3 ** x for x in range(9)]

print(cub3) # Output: [1, 3, 9, 27, 81, 243, 729, 2187, 6561]
```
Tương đương với
```
cub3 = []
for x in range (9):
cub3.append(3**x)
print(cub3)
```

Ngoài `for`, `if` cũng có thể được sử dụng trong một `list comprehension của Python`. Lệnh if có thể lọc các phần tử trong list hiện tại để tạo thành list mới như ví dụ sau:
```
cub3 = [3 ** x for x in range(9) if x > 4]
print(cub3) # Output: [243, 729, 2187, 6561]

so_le = [x for x in range (18) if x % 2 == 1]
print(so_le) # Output: [1, 3, 5, 7, 9, 11, 13, 15, 17]

noi_list = [x+y for x in ['Ngôn ngữ ','Lập trình '] for y in ['Python','C++']]

print(noi_list) # Output: ['Ngôn ngữ Python', 'Ngôn ngữ C++', 'Lập trình Python', 'Lập trình C++']
```

## 1.5 Các hàm Python tích hợp với list
Các hàm Python tích hợp sẵn như `all()`, `any()`, `enumerate()`, `len()`, `max()`, `min()`, `list()`, `sorted()`,... thường được sử dụng với list để thực hiện những nhiệm vụ khác nhau.
- **all():** Trả về giá trị True nếu tất cả các phần tử của list đều là `true` hoặc list rỗng.
- **any():** Trả về `True` nếu có bất kỳ phần tử nào trong list là `true`. Nếu list rỗng hàm trả về giá trị `False`.
- **enumerate():** Trả về đối tượng enumerate, chứa index và giá trị của tất cả các phần tử của list dưới dạng tuple.
- **len()**: Trả về độ dài (số lượng phần tử) của list.
- **list():** Chuyển đổi một đối tượng có thể lặp (tuple, string, set, dictionary) thành list.
- **max():** Trả về phần tử lớn nhất trong list.
- **min():** Trả về phần tử nhỏ nhất trong list.
- **sorted():** Trả về list mới đã được sắp xếp.
- **sum():** Trả về tổng của tất cả các phần tử trong list.

# 2. Tuple
Tuple trong Python là một chuỗi các phần tử có thứ tự giống như list. Sự khác biệt giữa list và tuple là chúng ta không thể thay đổi các phần tử trong tuple khi đã gán, nhưng trong list thì các phần tử có thể thay đổi.

Tuple thường được sử dụng cho các dữ liệu không cho phép sửa đổi và nhanh hơn list vì nó không thể thay đổi tự động. Một tuple được định nghĩa bằng dấu ngoặc đơn (), các phần tử trong tuple cách nhau bằng dấu phẩy (,).

Ví dụ
```
t = (10, "quan tri mang", 2j)
```

Chúng ta có thể sử dụng toán tử cắt [] để trích xuất phần tử trong tuple nhưng không thể thay đổi giá trị của nó.
```
t = (10, "quan tri mang", 2j)
print("t[0:2] = ", t[0:2]) #t[0:2] = (10, 'quan tri mang')
```

## 5.1 Tuple hơn list ở điểm nào?
Vì tuple và list khá giống nhau, nên chúng thường được sử dụng trong những tình huống tương tự nhau. Tuy nhiên, tuple vẫn có những lợi thế nhất định so với list, như:
- Tuple thường được sử dụng cho các kiểu dữ liệu không đồng nhất (khác nhau) và list thường sử dụng cho các kiểu dữ liệu (đồng nhất) giống nhau.
- Vì tuple không thể thay đổi, việc lặp qua các phần tử của tuple nhanh hơn so với list. Vì vậy, trong trường hợp này tuple chiếm ưu thế về hiệu suất hơn list một chút.
- Tuple chứa những phần tử không thay đổi, có thể được sử dụng như key cho dictionary. Với list, điều này không thể làm được.
- Nếu có dữ liệu không thay đổi việc triển khai nó như một tuple sẽ đảm bảo rằng dữ liệu đó được bảo vệ chống ghi (write-protected).

## 5.2 Tạo một tuple
Tuple được tạo bằng cách đặt tất cả các phần tử của nó trong dấu ngoặc đơn (), phân tách bằng dấu phẩy. Bạn có thể bỏ dấu ngoặc đơn nếu muốn, nhưng nên thêm nó vào cho code rõ ràng hơn.

Tuple không bị giới hạn số lượng phần tử và có thể có nhiều kiểu dữ liệu khác nhau như số nguyên, số thập phân, list, string,...
```
# Tuple rỗng
my_tuple = ()
print(my_tuple) # Output: ()

# tuple số nguyên
my_tuple = (2, 4, 16, 256)
print(my_tuple) # Output: (2, 4, 16, 256)

# tuple có nhiều kiểu dữ liệu
my_tuple = (10, "Quantrimang.com", 3.5)
print(my_tuple) # Output: (10, "Quantrimang.com", 3.5)

# tuple lồng nhau
my_tuple = ("QTM", [2, 4, 6], (3, 5, 7))
print(my_tuple) # Output: ("QTM", [2, 4, 6], (3, 5, 7))

# tuple có thể được tạo mà không cần dấu ()
# còn gọi là đóng gói tuple
my_tuple = 10, "Quantrimang.com", 3.5
print(my_tuple) # Output: (10, "Quantrimang.com", 3.5)

# mở gói (unpacking) tuple cũng có thể làm được
a, b, c = my_tuple
print(a) # Output: 10
print(b) # Output: Quantrimang.com
print(c)  # Output: 3.5
```
Tạo tuple chỉ có một phần tử hơi phức tạp chút, nếu bạn tạo theo cách thông thường là cho phần tử đó vào trong cặp dấu () là chưa đủ, cần phải thêm dấu phẩy để chỉ ra rằng, đây là tuple.
```
# tạo tuple chỉ với ()
my_tuple = ("Quantrimang.com")
print(type(my_tuple)) # Output: <class 'str'>

# khi thêm dấu phẩy vào cuối
my_tuple = ("Quantrimang.com",) 
print(type(my_tuple)) # Output: <class 'tuple'>

# dấu () là tùy chọn, bạn có thể bỏ nếu thích
my_tuple = "Quantrimang.com",
print(type(my_tuple)) # Output: <class 'tuple'>
```

## 5.3 Truy cập vào các phần tử của tuple
Có nhiều cách khác nhau để truy cập vào các phần tử của một tuple, khá giống với list, nên chúng ta có thể xem lại ở phần list.

**Index:** Sử dụng toán tử index [] để truy cập vào phần tử trong tuple với index bắt đầu bằng 0. Nghĩa là nếu tuple có 6 phần tử thì index của nó sẽ bắt đầu từ 0 đến 5. Nếu cố gắn truy cập đến index 6, 7 thì sẽ tạo lỗi IndexError. Index bắt buộc phải là số nguyên, mà không thể là số thập phân hay bất kỳ kiểu dữ liệu nào khác, nếu không sẽ tạo lỗi TypeError. Những tuple lồng nhau được truy cập bằng cách sử dụng index lồng nhau:
```
# tuple lồng nhau
n_tuple = ("Quantrimang.com", [2, 6, 8], (1, 2, 3))

# index lồng nhau
print(n_tuple[0][5]) # Output: 'r'

# index lồng nhau
print(n_tuple[1][2]) # Output: 8
```
**Index âm:** Python cho phép lập chỉ mục âm cho các đối tượng dạng chuỗi. Index -1 tham chiếu đến phần tử cuối cùng, -2 là thứ 2 tính từ cuối tính lên.

**Cắt lát (slice):** Có thể truy cập đến một loạt phần tử trong tuple bằng cách sử dụng toán tử cắt lát : (dấu 2 chấm).

Ngoài ra để kiểm tra xem một phần tử đã tồn tại trong tuple hay chưa, duyệt qua các phần tử của tuple chúng ta cũng sử dung với từ khóa `in` và `for` như trong list.

## 5.4 Thay đổi một tuple
Không giống như list, tuple không thể thay đổi. Điều này có nghĩa là các phần tử của một tuple không thể thay đổi một khi đã được gán. Nhưng, nếu bản thân phần tử đó là một kiểu dữ liệu có thể thay đổi (như list chẳng hạn) thì các phần tử lồng nhau có thể được thay đổi. Chúng ta cũng có thể gán giá trị khác cho tuple (gọi là gán lại - reassignment).
```
my_tuple = (1, 3, 5, [7, 9])
my_tuple[1] = 9 # TypeError: 'tuple' object does not support item assignment

my_tuple[3][0] = 8
print(my_tuple) # Output: (1, 3, 5, [8, 9])

# Nếu cần thay đổi tuple hãy gán lại giá trị cho nó
my_tuple = ('q', 'u', 'a', 'n', 't', 'r', 'i', 'm', 'a', 'n', 'g')
print(my_tuple) # Output: ('q', 'u', 'a', 'n', 't', 'r', 'i', 'm', 'a', 'n', 'g')
```

Chúng ta có thể dùng toán tử + để nối 2 tuple, toán tử * để lặp lại tuple theo số lần đã cho. Cả + và * đều cho kết quả là một tuple mới.
```
# Nối 2 tuple
print((2, 4, 6) + (3, 5, 7)) # Output: (2, 4, 6, 3, 5, 7)

# Lặp lại tuple
print(("Quantrimang.com",) * 3) # Output: ('Quantrimang.com', 'Quantrimang.com', 'Quantrimang.com')
```

## 5.5 Xóa tuple
Các phần tử trong tuple không thể thay đổi nên chúng ta cũng không thể xóa, loại bỏ phần tử khỏi tuple. Nhưng việc xóa hoàn toàn một tuple có thể thực hiện được với từ khóa del như dưới đây:
```
QTM = ('q','u','a','n','t','r','i','m','a','n','g','.','c','o','m')

del QTM[3] # TypeError: 'tuple' object doesn't support item deletion

del QTM
print (QTM) # NameError: name 'QTM' is not defined
```

## 5.6 Phương thức và hàm dùng với tuple trong Python
Phương thức thêm phần tử và xóa phần tử không thể sử dụng với tuple, chỉ có 2 phương thức sau là dùng được:
- **count(x):** Đếm số phần tử x trong tuple.
- **index(x):** Trả về giá trị index của phần tử x đầu tiên mà nó gặp trong tuple.
```
QTM = ['q','u','a','n','t','r','i','m','a','n','g','.','c','o','m']

print(QTM.count('m')) # Output: 2
print(QTM.index('n')) # Output: 3
```
Các hàm dùng trong tuple khá giống với list, gồm có:
- **all():** Trả về giá trị True nếu tất cả các phần tử của tuple là true hoặc tuple rỗng.
- **any():** Trả về True nếu có bất kỳ phần tử nào của tuple là true, nếu tuple rỗng trả về False.
- **enumerated():** Trả về đối tượng enumerate (liệt kê), chứa cặp index và giá trị của tất cả phần tử của tuple.
- **len():** Trả về độ dài (số phần tử) của tuple.
- **max():** Trả về phần tử lớn nhất của tuple.
- **min():** Trả về phần tử nhỏ nhất của tuple.
- **sorted():** Lấy phần tử trong tuple và trả về list mới được sắp xếp (tuple không sắp xếp được).
- **sum():** Trả về tổng tất cả các phần tử trong tuple.
- **tuple():** Chuyển đổi những đối tượng có thể lặp (list, string, set, dictionary) thành tuple.

# 6. Set



#  Tham khảo
1. [https://quantrimang.com/hoc/gioi-thieu-qua-ve-chuoi-so-list-trong-python-140881](https://quantrimang.com/hoc/gioi-thieu-qua-ve-chuoi-so-list-trong-python-140881)