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

qtm_list[2.0] # TypeError: list indices must be integers or slices, not float
```

List lồng nhau sẽ được truy cập bằng index lồng nhau:
```
ln_list = ["Happy", [1,3,5,9]]

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

## 1.2 Các thao tác trên List
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

Output:
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

del my_list[1:7] # xóa phần tử có index từ 1 đến 7 (ko bao gồm index=7)
print(my_list) # Output: ['q', 'a', 'n', 'g', '.', 'c', 'o', 'm']

del my_list # xóa toàn bộ list my_list
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
my_tuple = ()
print(my_tuple) # Output: ()

my_tuple = (2, 4, 16, 256)
print(my_tuple) # Output: (2, 4, 16, 256)

my_tuple = (10, "Quantrimang.com", 3.5)
print(my_tuple) # Output: (10, "Quantrimang.com", 3.5)

my_tuple = ("QTM", [2, 4, 6], (3, 5, 7))
print(my_tuple) # Output: ("QTM", [2, 4, 6], (3, 5, 7))

my_tuple = 10, "Quantrimang.com", 3.5
print(my_tuple) # Output: (10, "Quantrimang.com", 3.5)

a, b, c = my_tuple
print(a) # Output: 10
print(b) # Output: Quantrimang.com
print(c)  # Output: 3.5
```
Tạo tuple chỉ có một phần tử hơi phức tạp chút, nếu bạn tạo theo cách thông thường là cho phần tử đó vào trong cặp dấu () là chưa đủ, cần phải thêm dấu phẩy để chỉ ra rằng, đây là tuple.
```
my_tuple = ("Quantrimang.com")
print(type(my_tuple)) # Output: <class 'str'>

my_tuple = ("Quantrimang.com",) 
print(type(my_tuple)) # Output: <class 'tuple'>

my_tuple = "Quantrimang.com",
print(type(my_tuple)) # Output: <class 'tuple'>
```

## 5.3 Truy cập vào các phần tử của tuple
Có nhiều cách khác nhau để truy cập vào các phần tử của một tuple, khá giống với list, nên chúng ta có thể xem lại ở phần list.

**Index:** Sử dụng toán tử index [] để truy cập vào phần tử trong tuple với index bắt đầu bằng 0. Nghĩa là nếu tuple có 6 phần tử thì index của nó sẽ bắt đầu từ 0 đến 5. Nếu cố gắn truy cập đến index 6, 7 thì sẽ tạo lỗi IndexError. Index bắt buộc phải là số nguyên, mà không thể là số thập phân hay bất kỳ kiểu dữ liệu nào khác, nếu không sẽ tạo lỗi TypeError. Những tuple lồng nhau được truy cập bằng cách sử dụng index lồng nhau:
```
n_tuple = ("Quantrimang.com", [2, 6, 8], (1, 2, 3))
print(n_tuple[0][5]) # Output: 'r'
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

my_tuple = ('q', 'u', 'a', 'n', 't', 'r', 'i', 'm', 'a', 'n', 'g')
print(my_tuple) # Output: ('q', 'u', 'a', 'n', 't', 'r', 'i', 'm', 'a', 'n', 'g')
```

Chúng ta có thể dùng toán tử + để nối 2 tuple, toán tử * để lặp lại tuple theo số lần đã cho. Cả + và * đều cho kết quả là một tuple mới.
```
print((2, 4, 6) + (3, 5, 7)) # Output: (2, 4, 6, 3, 5, 7)
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
Set trong Python là tập hợp các phần tử duy nhất, không có thứ tự. Các phần tử trong set phân cách nhau bằng dấu phẩy và nằm trong dấu ngoặc nhọn {}. Nhớ kỹ rằng các phần tử trong set không có thứ tự. Nhưng các phần tử trong set có thể thay đổi, có thể thêm hoặc xóa phần tử của set. Set có thể được sử dụng để thực hiện các phép toán như tập hợp, giao,...

## 6.1 Cách tạo set
Set được tạo bằng cách đặt tất cả các phần tử trong dấu ngoặc nhọn, phân tách bằng dấu phẩy hoặc sử dụng hàm set(). Set không giới hạn số lượng phần tử, nó có thể chứa nhiều kiểu biến khác nhau, nhưng không thể chứa phần tử có thể thay đổi được như list, set hay dictionary.
```
a = {5,2,3,1,4}
print("a=", a) # Output: a = {1, 2, 3, 4, 5}

my_set = {1.0, "Xin chào", (1, 2, 3)}
print("QTM_Set=",my_set) #Output: QTM_Set= {'Xin chào', 1.0, (1, 2, 3)}
```

Tạo set rỗng có chút khó khăn. Cặp dấu {} sẽ tạo một dictionary trong Python. Để tạo set không có phần tử nào, ta sử dụng hàm set() mà không có đối số nào.
```
qtm = {} # initialize a with {}
print(type(qtm)) # Output: <class 'dict'>

qtm = set() # Khởi tạo qtm với set()
print(type(qtm)) # Output: <class 'set'>
```

## 6.2 Thay đổi set trong Python
Vì set là tập hợp các phần tử không có thứ tự nên chỉ mục không ý nghĩa gì với set. Toán tử cắt [] sẽ không làm việc trên set. Nếu cố tình dùng, bạn sẽ nhận được thông báo lỗi như dưới đây:
```
>>> a[1]
Traceback (most recent call last):
File "<pyshell#2>", line 1, in <module>
a[1]
TypeError: 'set' object does not support indexing
```

Để thêm một phần tử vào set, bạn sử dụng add() và để thêm nhiều phần tử dùng update(). Update() có thể nhận tuple, list, strring và set làm đối số. Trong mọi trường hợp, Set có giá trị duy nhất, các bản sao sẽ tự động bị loại bỏ.
```
my_set = {1,3}
my_set.add(2)
print(my_set) # Output: {1, 2, 3}

my_set.update([2,3,4])
print(my_set) # Output: {1, 2, 3, 4}

my_set.update([4,5], {1,6,8})
print(my_set) # Output: {1, 2, 3, 4, 5, 6, 8}
```

## 6.3 Tìm kiếm, duyệt qua set
Kiểm tra một đối tượng xem nó có nằm trong set không, sử dụng từ khóa `in`.
```
my_set = set("Quantrimang.com")
print('Q' in my_set) # Output: True
print('q' in my_set) # Output: False
```

Sử dụng vòng lặp for để duyệt qua các phần tử của set.
```
for letter in set("Python"):
print(letter) # Output: Các ký tự của chuỗi Python
```

## 6.4 Xóa phần tử khỏi set
Chúng ta dùng discard() và remove() để xóa phần tử cụ thể khỏi set. Khi phần tử cần xóa không tồn tại trong set thì discard() không làm gì cả, còn remove() sẽ báo lỗi.
```
my_set = {1, 3, 4, 5, 6}

my_set.discard(4)
print(my_set) # Output: {1, 3, 5, 6}

my_set.remove(6)
print(my_set) # Output: {1, 3, 5}

my_set.discard(2)
print(my_set) # Output: {1, 3, 5}

my_set.remove(2) # Output: KeyError: 2
```

Bạn có thể xóa và trả lại một phần tử bằng phương thức pop(). Set không có thứ tự, không có cách nào để xác định phần tử nào sẽ bị xóa, điều này diễn ra hoàn toàn ngẫu hứng. Việc xóa hoàn toàn set được thực hiện bằng cách dùng clear().
```
my_set = set("Quantrimang.com")
print(my_set) # Output: set of unique elements

print(my_set.pop()) # Output: phần tử bị xóa ngẫu nhiên

my_set.pop()
print(my_set) # Output: phần tử bị xóa ngẫu nhiên

my_set.clear()
print(my_set) #Output: set()
```

## 6.5 Các toán tử set trong Python
Set thường được sử dụng để chứa các toán tử tập hợp như hợp, giao, hiệu, bù. Có cả phương thức và toán tử để thực hiện những phép toán tập hợp này.

**Hợp của A và B** là tập hợp tất cả các phần tử của A và B. Hợp được biểu diễn bằng cách sử dụng toán tử | hoặc sử dụng phương thức union().
```
A = {1, 2, 3, 4, 5}
B = {4, 5, 6, 7, 8}

print(A | B) # Output: {1, 2, 3, 4, 5, 6, 7, 8}

print(A.union(B)) # Output: {1, 2, 3, 4, 5, 6, 7, 8}
print(B.union(A)) # Output: {1, 2, 3, 4, 5, 6, 7, 8}
```

**Giao của A và B** là tập hợp những phần tử chung của A và B. Để tìm giao của A và B ta có thể dùng toán tử & hoặc hàm intersection().
```
A = {1, 2, 3, 4, 5}
B = {4, 5, 6, 7, 8}

print(A & B) # Output: {4, 5}

print(A.intersection(B)) # Output: {4, 5}
print(B.intersection(A)) # Output: {4, 5}
```

**Hiệu của A và B (A-B)** là tập hợp phần tử chỉ có trong A, không có trong B. **Hiệu của B và A (B-A)** là tập hợp phần tử chỉ có trong B không có trong A. Có thể sử dụng toán tử - hoặc hàm difference() để thực hiện phép toán tập hợp này.
```
A = {1, 2, 3, 4, 5}
B = {4, 5, 6, 7, 8}

print(A - B) # Output: {1, 2, 3}
print(A.difference(B)) # Output: {1, 2, 3}

print(B - A) # Output: {8, 6, 7}
print(B.difference(A)) # Output: {8, 6, 7}
```

**Bù của A và B** là tập hợp những phần tử có trong A và B nhưng không phải phần tử chung của hai tập hợp này. Bạn có thể dùng toán tử ^ hoặc hàm symmetric_difference() để thực hiện phép bù.
```
A = {1, 2, 3, 4, 5}
B = {4, 5, 6, 7, 8}

print(A ^ B) # Output: {1, 2, 3, 6, 7, 8}
print(A.symmetric_difference(B)) # Output: {1, 2, 3, 6, 7, 8}
```

## 6.6 Các phương thức dùng trên set
- **add():** Thêm một phần tử vào set.
- **clear():** Xóa tất cả phần tử của set.
- **copy():** Trả về bản sao chép của set.
- **difference():**	Trả về set mới chứa những phần tử khác nhau của 2 hay nhiều set.
- **difference_update():** Xóa tất cả các phần tử của set khác từ set này.
- **discard():** Xóa phần tử nếu nó có mặt trong set.
- **intersection():** Trả về set mới chứa phần tử chung của 2 set.
- **intersection_update():** Cập nhật set với phần tử chung của chính nó và set khác.
- **isdisjoint():**	Trả về True nếu 2 set không có phần tử chung.
- **issubset():** Trả về True nếu set là tập con của set khác.
- **issuperset():**	Trả về True nếu set này chứa set khác.
- **pop():** Xóa và trả về phần tử ngẫu nhiên, báo lỗi KeyError nếu set rỗng.
- **remove():**	Xóa phần tử từ set. Nếu phần tử đó không có trong set sẽ báo lỗi KeyError.
- **symmetric_difference():** Trả về set mới chứa những phần tử không phải là phần tử chung của 2 set.
- **symmetric_difference_update():**	Cập nhật set với những phần tử khác nhau của chính nó và set khác.
- **union():** Trả về set mới là hợp của 2 set.
- **update():**	Cập nhật set với hợp của chính nó và set khác.

## 6.7 Hàm thường dùng trên set
Các hàm thường dùng trên set bao gồm `all()`, `any()`, `enumerate()`, `len()`, `max()`, `min()`, `sorted()`, `sum()`. Chức năng của những hàm này khá giống với khi bạn sử dụng trên list, tuple, chúng ta có thể tham khảo thêm từ các phần này.

## 6.8 Frozenset trong Python
Frozenset là một lớp mới, có đặc điểm của một set, nhưng phần tử của nó không thể thay đổi được sau khi gán. Để dễ hình dung thì tuple là list bất biến còn frozenset là set bất biến.

Các set có thể thay đổi được nhưng không thể băm (hash) được, do đó không thể sử dụng set để làm key cho dictionary. Nhưng frozenset có thể băm được nên có thể dùng như các key cho dictionary.

Frozenset có thể tạo bằng hàm frozenset(). Kiểu dữ liệu này hỗ trợ các phương thức như copy(), difference(), intersection(), isdisjoint(), issubset(), issuperset(), symmetric_difference() và union(). Vì không thể thay đổi nên phương thức add() hay remove() không sử dụng được trên frozenset.

# 7. Dictionary
Dictionary là tập hợp các cặp khóa giá trị không có thứ tự. Nó thường được sử dụng khi chúng ta có một số lượng lớn dữ liệu. Các dictionary được tối ưu hóa để trích xuất dữ liệu với điều kiện bạn phải biết được khóa để lấy giá trị.

## 7.1 Cách tạo dictionary trong Python
Trong Python, dictionary được định nghĩa trong dấu ngoặc nhọn {} với mỗi phần tử là một cặp theo dạng key:value. Key và value này có thể là bất kỳ kiểu dữ liệu nào. Bạn cũng có thể tạo dictionary bằng cách sử dụng hàm dict() được tích hợp sẵn.
```
dict1 = {} #dictionary rỗng
dict2 = {1: 'Quantrimang.com',2: 'Công nghệ'}
dict3 = {'tên': 'QTM', 1: [1, 3, 5]}
dict4 = dict({1:'apple', 2:'ball'})
dict5 = dict([(1,'QTM'), (2,'CN')])
```
```
>>> type(dict2)
<class 'dict'>
```

## 7.2 Truy cập phần tử của dictionary
Các kiểu dữ liệu lưu trữ khác sử dụng index để truy cập vào các giá trị thì dictionary sử dụng các key. Key có thể được sử dụng trong cặp dấu ngoặc vuông hoặc sử dụng get().

Ví dụ
```
dict2 = {1: 'Quantrimang.com','quantrimang': 'Công nghệ'} 
print(type(dict2)) #in kiểu dữ liệu của dict2

print("dict2[1] = ", dict2[1]) 
print("dict2[quantrimang] = ",dict2['quantrimang'])
```
Kết quả
```
<class 'dict'>
dict2[1] = Quantrimang.com
dict2[quantrimang] = Công nghệ
```

## 7.3 Thay đổi, thêm phần tử cho dictionary
Dictionary có thể thay đổi, nên có thể thêm phần tử mới hoặc thay đổi giá trị của các phần tử hiện có bằng cách sử dụng toán tử gán. Nếu key đã có, giá trị sẽ được cập nhật, nếu là một cặp key: value mới thì sẽ được thêm thành phần tử mới.
```
dict2 = {1: 'Quantrimang.com','quantrimang': 'Công nghệ'}

dict2['quantrimang'] = 'Quản trị mạng'
print(dict2) #output: {1: 'Quantrimang.com', 'quantrimang': 'Quản trị mạng'}

dict2[2] = 'Python'
print(dict2) #output: {1: 'Quantrimang.com', 'quantrimang': 'Quản trị mạng', 2: 'Python'}
```

## 7.4 Kiểm tra và duyệt qua phần tử trong dictionary
Kiểm tra key của phần tử đã có trong dictionary hay chưa bằng cách dùng in, và không thể làm điều đó với value.
```
lap_phuong = {0: 0, 1: 1, 2: 8, 3: 27, 4: 64, 5: 125}
print (2 in lap_phuong) #output: True
print (9 in lap_phuong) #output: False
print (5 not in lap_phuong) #output: False
```
Dùng vòng lặp for để duyệt qua key của các phần tử trong dictionary.
```
lap_phuong = {0: 0, 1: 1, 2: 8, 3: 27, 4: 64, 5: 125}
for i in lap_phuong
    print(lap_phuong[i]) # Output: Các giá trị trong dictionary
```

## 7.5 Xóa phần tử từ dictionary
Bạn có thể xóa phần tử cụ thể của dictionary bằng cách sử dụng pop(), nó sẽ xóa phần tử có key đã cho và trả về giá trị của phần tử. popitem() có thể xóa và trả về một phần tử tùy ý dưới dạng (key, value). Tất cả các phần tử trong dictionary có thể bị xóa cùng lúc bằng cách dùng clear(). Ngoài ra, từ khóa del cũng có thể dùng để xóa một phần tử hoặc toàn bộ dictionary.
```
binh_phuong = {1:1, 2:4, 3:9, 4:16, 5:25}

print(binh_phuong.pop(4)) # Output: 16
print(binh_phuong) # Output: {1: 1, 2: 4, 3: 9, 5: 25}

del binh_phuong[2]
print(binh_phuong) # output: {1: 1, 3: 9, 5: 25}

print(binh_phuong.popitem()) # Output: (5, 25), xóa bất kỳ ở đây là (5, 25)
print(binh_phuong) # Output: {1: 1, 3: 9}

binh_phuong.clear()
print(binh_phuong) # output: {}

del binh_phuong
print(squares) # Thông báo lỗi
```

## 7.6 Dictionary comprehension trong Python
Dictionary comprehension là cách đơn giản, rút gọn để tạo dictionary mới từ một vòng lặp trong Python. Câu lệnh sẽ bao gồm một cặp biểu thức (key:value) cùng câu lệnh for, tất cả đặt trong dấu {}. Dưới đây là ví dụ tạo dictionary với mỗi pahàn tử là một cặp số và lập phương của nó.
```
lap_phuong = {x: x*x*x for x in range(6)}
print(lap_phuong) # Output: {0: 0, 1: 1, 2: 8, 3: 27, 4: 64, 5: 125}
```

Câu lệnh trên tương đương với đoạn code
```
lap_phuong = {}
for x in range(6):
    lap_phuong[x] = x*x*x
print(lap_phuong)
```

Chúng ta cũng có thể sử dụng lệnh if trong dictionary comprehension. Lệnh if có thể lọc những phần tử trong dictionary hiện có để tạo thành dictionary mới như ví dụ dưới đây:
```
lap_phuong_chan = {x: x*x*x for x in range (10) if x%2==0}
print(lap_phuong_chan) # output: {0: 0, 2: 8, 4: 64, 6: 216, 8: 512}
```

#  Tham khảo
1. [https://quantrimang.com/hoc/gioi-thieu-qua-ve-chuoi-so-list-trong-python-140881](https://quantrimang.com/hoc/gioi-thieu-qua-ve-chuoi-so-list-trong-python-140881)