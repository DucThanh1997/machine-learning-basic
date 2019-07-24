Thực ra nó gôm các bước
- Nhìn tổng thể vấn đề
- Thu thập dữ liệu
- Khám phá và mô hình hóa để có cái nhìn cụ thể và sâu sắc hơn 
- Chuẩn bị data cho thuật toán ML
- Chọn model và train nó
- Tinh chỉnh model
- Giới thiệu giải pháp của bạn
- Chạy, giám sát và duy trì hệ thống


## Tìm vấn đề
- Điều đầu tiên cần làm là tìm rõ mục đích kinh doanh của công ty để có thể chọn thuật toán cũng như model hợp lí nhất

**data pipeline**: 1 chuỗi các thành phần xử lí dữ liệu được gọi là data pipeline

Các thành phần thường chạy không đồng bộ. Mỗi thành phần lấy một lượng lớn dữ liệu rồi xử lý dữ liệu và tạo ra kết quả trong 
kho lưu trữ dữ liệu khác và sau đó một thời gian, thành phần tiếp theo trong đường ống sẽ kéo dữ liệu này ra và tạo ra đầu ra 
của chính nó

Mỗi thành phần khá khép kín: giao diện giữa các thành phần chỉ đơn giản là lưu trữ dữ liệu. 
Điều này giúp cho hệ thống khá đơn giản để nắm bắt (với sự trợ giúp của biểu đồ luồng dữ liệu) và 
các nhóm khác có thể tập trung vào các thành phần còn lại . Hơn nữa, nếu một thành phần bị hỏng, 
các thành phần hạ lưu thường có thể tiếp tục chạy bình thường (ít nhất là trong một thời gian) chỉ bằng cách 
sử dụng đầu ra cuối cùng từ thành phần bị hỏng. Điều này giúp cho hệ thống kiến trúc khá mạnh mẽ.

- Câu hỏi tiếp theo là giải pháp hiện tại trông như thế nào (nếu có). Nó thường sẽ cung cấp cho bạn một hiệu suất tham khảo,
cũng như hiểu biết về cách giải quyết vấn đề.

### Chọn thước đo hiệu năng
Thường thì người ta sẽ dùng Root Mean Square Error (RMSE) làm thước đo hiệu năng 

Công thức
![image](https://user-images.githubusercontent.com/45547213/61774445-10c4d680-ae21-11e9-9da2-81ed0a968e95.png)

Kí hiệu: 
- m là số biến trong bộ training set
- x(i) là vecotor chỉ số liệu của các biến đó ví dụ biên 1 có x(1) = (5, 10, 15, 20)
- y(i) là giá trị chuẩn (label đó)
- X là ma trận chứa tất cả các vector x(i) đã được chuyển vị
- h là hàm dự đoán của hệ thống. Khi hệ thống được đưa cho 1 biến dữ liệu chứa các dữ liệu x(i), nó cho ra cái giá trị dự đoán
![image](https://user-images.githubusercontent.com/45547213/61774944-1ff85400-ae22-11e9-934f-94f22734cbdd.png)

- RMSE(X, h) là hàm chi phí được đo trên tập hợp các ví dụ sử dụng giả thuyết của bạn h.

Thường thì người ta sẽ dùng RMSE cho `regression task` nhưng nếu tập dữ liệu của bạn có quá nhiều biến bị outlier(ngoại lệ) thì
chúng ta dùng Mean Absolute Error

![image](https://user-images.githubusercontent.com/45547213/61775476-3521b280-ae23-11e9-801b-dea1ad223178.png)

Cả RMSE và MAE đều là cách để đo khoảng cách giữa hai vectơ: vectơ dự đoán và vectơ của các giá trị đích.

## Sờ mó vào dữ liệu sơ khai

```
import pandas as pd
path = "C:\\Users\\Thanh\\Downloads\\california-housing-prices\\housing.csv"
housing = pd.read_csv(path)

housing.head(): In ra năm bản ghi đầu
housing.info(): In ra các kiểu dữ liệu trong bảng có
housing.describe(): In ra mấy cái count, min, max, mean của tập dữ liệu
```

Hoặc bạn có thể in ra mô hình nhìn cho ló trực quan


































