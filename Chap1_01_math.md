## Chuyển vị và Hermitian
**Định nghĩa**: Về cơ bản chuyển vị nó như kiểu đổi từ ngang thành dọc, dọc thành ngang nhưng mà với số phức thường có thêm cả chuyển vị liên
hợp

![image](https://user-images.githubusercontent.com/45547213/61581519-84c55d00-ab49-11e9-9052-945cf994c305.png)

## Nhân 2 ma trận
**Điều kiện**: Để nhân 2 ma trận số cột của ma trận thứ nhất phải bằng số hàng của ma trận thứ
hai. Trong ví dụ trên, chúng đều bằng n.

**Cách tính**: cột 1 nhân hàng 1 ra vị trí C11, cột 1 nhân hàng 2 ra vị trí C12
![image](https://user-images.githubusercontent.com/45547213/61581592-a4a95080-ab4a-11e9-9fae-ef85659f3e5d.png)

**Các tính chất**:
1. Phép nhân ma trận không có tính chất giao hoán. Thông thường (không phải luôn luôn),
AB 6= BA. Thậm chí, trong nhiều trường hợp, các phép tính này không tồn tại vì kích
thước các ma trận lệch nhau.
2. Phép nhân ma trận có tính chất kết hợp: ABC = (AB)C = A(BC)
3. Phép nhân ma trận có tính chất phân phối đối với phép cộng: A(B + C) = AB + AC.
4. Chuyển vị của một tích bằng tích các chuyển vị theo thứ tự ngược lại. Điều tương tự xảy
ra với Hermitian của một tích:


## Ma trận đơn vị, ma trận nghịch đảo
### Ma trận đơn vị
- Là kiểu ma trận mà tất cả đều bằng 0 trừ đường chéo chính là 1 Kí hiệu là I

### Ma trận nghịch đảo
- Là ma trận là 2 ma trận nhân với nhau ra ma trận đơn vị

## Ma trận đặc biệt
### Ma trận đường chéo
- Là ngoài các phần tử ở trên đường chéo ra thì phần tử nào cũng bằng 0

### Ma trận tam giác
- Một ma trận vuông được gọi là ma trận tam giác trên (upper triangular matrix ) nếu tất cả
các thành phần nằm phía dưới đường chéo chính bằng 0. Tương tự, một ma trận vuông được
gọi là ma trận tam giác dưới (lower triangular matrix ) nếu tất cả các thành phần nằm phía
trên đường chéo chính bằng 0.

## Định thức
![image](https://user-images.githubusercontent.com/45547213/61582295-551b5280-ab53-11e9-8bd1-7a3cac39cb02.png)
**tính chất**:
1. det(A) = det(AT

): Một ma trận bất kỳ và chuyển vị của nó có định thức như nhau.
2. Định thức của một ma trận đường chéo (và vuông) bằng tích các phần tử trên đường chéo
chính. Nói cách khác, nếu A = diag(a1, a2, . . . , an), thì det(A) = a1a2 . . . an.
3. Định thức của một ma trận đơn vị bằng 1.
4. Định thức của một tích bằng tích các định thức.

det(AB) = det(A) det(B) (1.12)

với A, B là hai ma trận vuông cùng chiều.
5. Nếu một ma trận có một hàng hoặc một cột là một vector 0, thì định thức của nó bằng 0.
6. Một ma trận là khả nghịch khi và chỉ khi định thức của nó khác 0.
7. Nếu một ma trận khả nghịch, định thức của ma trận nghịch đảo của nó bằng nghịch đảo
định thức của nó.

![image](https://user-images.githubusercontent.com/45547213/61582318-87c54b00-ab53-11e9-8ea5-fb5c0688317e.png)

## Tổ hợp tuyến tính và không gian sinh
### Tổ hợp tuyến tính (linear combination)
Đây là 1 tổ hợp tuyến tính
![image](https://user-images.githubusercontent.com/45547213/61582352-03bf9300-ab54-11e9-85ce-af02628f7254.png)

### Cơ sở của 1 không gian
Một hệ các vector {a1, . . . , an} trong không gian vector m chiều V = R

m được gọi là một cơ sở (basic) nếu hai điều kiện sau được thoả mãn:
1. V ≡ span(a1, . . . , an)
2. {a1, . . . , an} là một hệ độc lập tuyến tính.

Khi đó, mọi vector b ∈ V đều có thể biểu diễn duy nhất dưới dạng một tổ hợp tuyến tính
của các ai.

Từ hai tính chất cuối ở mục trước, ta có thể suy ra rằng m = n.


## Hạng của ma trận
**Định nghĩa**: là số hàng không bằng 0 nếu số hàng toàn số 0 thì nó ko được tính là 1 hạng
**Tính chất**: 
1. Một ma trận có hạng bằng 0 khi và chỉ khi nó là ma trận 0.
2. rank(A) = rank(AT). 

Hạng của một ma trận bằng hạng của ma trận chuyển vị. Nói cách
khác, số lượng lớn nhất các cột độc lập tuyến tính của một ma trận bằng với số lượng
lớn nhất các hàng độc lập tuyến tính của ma trận đó. Từ đây ta suy ra:
3. Nếu A ∈ R
m×n
, thì rank(A) ≤ min(m, n) vì theo định nghĩa, hạng của một ma trận

không thể lớn hơn số hàng hoặc số cột của nó.
4. rank(AB) ≤ min(rank(A),rank(B))
5. rank(A + B) ≤ rank(A) + rank(B). Điều này chỉ ra rằng một ma trận có hạng bằng k
không được biểu diễn dưới dạng ít hơn k ma trận có hạng bằng 1. Đến bài Singular Value
Decomposition, chúng ta sẽ thấy rằng một ma trận có hạng bằng k có thể biểu diễn được
dưới dạng đúng k ma trận có hạng bằng 1.
6. Bất đẳng thức Sylvester về hạng: Nếu A ∈ R
m×n
, B ∈ R
n×k
, thì
rank(A) + rank(B) − n ≤ rank(AB)






































