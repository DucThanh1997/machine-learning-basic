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

## Ma trận trực giao
**Định nghĩa**: Ma trận trực giao là ma trận thỏa mãn điều kiện 

![image](https://user-images.githubusercontent.com/45547213/61589271-e03b2d80-abd1-11e9-9344-08cf1da9ccaf.png)

tức là ma trận chuyển vị của A cũng là ma trận nghịch đảo của A

ma trận chuyển vị là ma trận biến đổi từ ngang thành dọc của ma trận cũ

ma trận nghịch đảo là khi nhân với ma trận gốc ra ma trận đơn vị

**Tính chất**:

![image](https://user-images.githubusercontent.com/45547213/61589327-8f780480-abd2-11e9-966b-62cb521063d2.png)

## Trị riêng và vector riêng
**Định nghĩa**: 


![image](https://user-images.githubusercontent.com/45547213/61589458-3c9f4c80-abd4-11e9-9c74-15b3bf4b7bde.png)

**Tính chất**:

1. Nếu x là một vector riêng của A ứng với λ thì kx, ∀k 6= 0 cũng là vector riêng ứng với
trị riêng đó. Nếu x1, x2 là hai vector riêng ứng với cùng trị riêng λ, thì tổng của chúng
cũng là một vector ứng với trị riêng đó. Từ đó suy ra tập hợp các vector riêng ứng với
một trị riêng của một ma trận vuông tạo thành một không gian vector con, thường được
gọi là không gian riêng (eigenspace) ứng với trị riêng đó.
2. Mọi ma trận vuông bậc n đều có n trị riêng (kể cả lặp) và có thể là các số phức.
3. Tích của tất cả các trị riêng của một ma trận bằng định thức của ma trận đó. Tổng tất
cả các trị riêng của một ma trận bằng tổng các phần tử trên đường chéo của ma trận đó.
4. Phổ của một ma trận bằng phổ của ma trận chuyển vị của nó.
5. Nếu A, B là các ma trận vuông cùng bậc thì pAB(t) = pBA(t). Điều này nghĩa là, mặc
dù tích của hai ma trận không có tính chất giao hoán, đa thức đặc trưng của AB và BA
là như nhau. Tức phổ của hai tích này là trùng nhau.
6. Với ma trận đối xứng (hoặc tổng quát, Hermitian), tất cả các trị riêng của nó đều là các
số thực. Thật vậy, giả sử λ là một trị riêng của một ma trận Hermitian A và x là một
vector riêng ứng với trị riêng đó. 


**Cách tìm trị riêng**
 
 - Tìm det(A- λ*I)
 với I là ma trận đơn vị
 
 - Cho det bằng 0 rồi tìm ra λ đó là trị riêng

**Cách tím vector riêng**

![image](https://user-images.githubusercontent.com/45547213/61611947-61083100-ac87-11e9-85ea-6e9251716c70.png)

 ## Chéo hóa ma trận
 - tìm điều kiện của ma trận vuông cấp n
  + phải có n trị riêng nếu ko có n trị riêng thì ko treo hóa được
  + phải có n vector riêng
  + phải là 1 ma trận vuông

 - Cách làm
 Giả sử A là ma trận chéo hóa được. Khi đó ta tìm ma trận C sao cho C^{-1}AC  là ma trận đường chéo như thế nào?

Điều này đã được mô tả chi tiết trong cuốn Toán cao cấp tập 1 của Nguyễn Đình Trí, và những cuốn sách tương tự. Ở đây, tôi cung cấp thêm chi tiết.

Cấu tạo của C gồm n cột, mỗi cột là một vector riêng của A, sao cho n cột này phải độc lập tuyến tính. Để tiện trình bày chứng minh, tôi xét trường hợp n=3. Khi đó ta viết C=[C_1|C_2|C_3] với C_i là các cột của ma trận C cỡ 3\times 3.

Nhắc lại là các cột C_i  là vector riêng của A ứng với giá trị riêng \lambda_i.

Ta có AC=[AC_1|AC_2|AC_3] = [\lambda_1C_1|\lambda_2 C_2| \lambda_3 C_3]. Từ đó suy ra C^{-1}AC = [\lambda_1 C^{-1}C_1|\lambda_2 C^{-1}C_2|\lambda_3 C^{-1}C_3].

Vậy C^{-1}C_i bằng bao nhiêu? Rất đơn giản, nhận xét: I = C^{-1}C = [C^{-1}C_1|C^{-1}C_2|C^{-1}C_3] với I là ma trận đồng nhất.

Như vậy, C^{-1}C_1=\begin{bmatrix}1\\ 0\\ 0\end{bmatrix} và tương tự với các cột còn lại. Cũng từ điều này, ta đã chứng minh xong kết quả C^{-1}AC = \begin{bmatrix}\lambda_1 &0 &0 \\ 0&\lambda_2 &0 \\ 0 & 0 &\lambda_3\end{bmatrix}.































