## Linear Regression
Tổng quát hơn, một mô hình tuyến tính đưa ra dự đoán bằng cách tính toán tổng các trọng số của các tính năng đầu vào, 
cộng với một hằng số được gọi là thuật ngữ thiên vị (còn gọi là thuật ngữ chặn), như được thể hiện trong Công thức 4-1.

![image](https://user-images.githubusercontent.com/45547213/62119503-f0e25680-b2e9-11e9-81ac-28999c5b95af.png)

- y^ là giá trị dự đoán
- n là số lượng thuộc tính
- xi là giá trị chỉ thứ tự thuộc tính
- cái thê ta là cái trọng số bias đó

Để đo lường độ chính xác của Linear Regression người ta dùng RMSE, chúng ta có thể giảm RMSE bằng cách điều chỉnh theta
có 2 cach điều chỉnh

Cái đầu tiên là:
## The Normal Equation
- Công thức:

![image](https://user-images.githubusercontent.com/45547213/62120279-7ca8b280-b2eb-11e9-938f-fbfd5ef380a3.png)

chạy
```
X_b = np.c_[np.ones((100, 1)), X] # add x0 = 1 to each instance
theta_best = np.linalg.inv(X_b.T.dot(X_b)).dot(X_b.T).dot(y)

X_new = np.array([[0], [2]])
X_new

X_new_b = np.c_[np.ones((2, 1)), X_new]
X_new_b

y_predict = X_new_b.dot(theta_best)
y_predict
```

```
Khi chạy trên thuật toán
```
from sklearn.linear_model import LinearRegression

lin_reg = LinearRegression()
lin_reg.fit(X, y)
lin_reg.intercept_, lin_reg.coef_
lin_reg.predict(X_new)
```
### Độ phức tạp của thuật toán
một khi bạn đã huấn luyện mô hình hồi quy tuyến tính (sử dụng phương trình bình thường hoặc bất kỳ thuật toán nào khác),
các dự đoán rất nhanh: độ phức tạp tính toán là tuyến tính liên quan đến cả số lượng trường hợp bạn muốn đưa ra dự đoán 
và số lượng tính năng . Nói cách khác, việc đưa ra dự đoán về số lần nhiều gấp đôi (hoặc gấp đôi số tính năng) sẽ
mất khoảng gấp đôi thời gian.


### Gradient Descent
nó đo độ dốc cục bộ của hàm lỗi liên quan đến vectơ tham số và nó đi theo hướng của độ dốc giảm dần. Khi độ dốc bằng 0, 
bạn đã đạt đến mức tối thiểu!

Cụ thể, bạn bắt đầu bằng cách điền với các giá trị ngẫu nhiên (đây được gọi là khởi tạo ngẫu nhiên),
và sau đó bạn cải thiện dần dần, thực hiện từng bước một, từng bước cố gắng giảm hàm chi phí (ví dụ: MSE),
cho đến khi thuật toán hội tụ đến mức tối thiểu

![image](https://user-images.githubusercontent.com/45547213/62140147-a9bd8b00-b314-11e9-87db-54a4c9edfb59.png)

Một tham số quan trọng trong Gradient Descent là kích thước của các bước, được xác định bởi siêu tham số tốc độ học tập. 
Nếu tốc độ học tập quá nhỏ, thì thuật toán sẽ phải trải qua nhiều lần lặp để hội tụ, sẽ mất nhiều thời gian



