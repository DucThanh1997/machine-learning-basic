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

## Tạo test set
- Có 1 cách lấy bộ test mà theo tôi là giải pháp okke nhất
  + dựa vào các cột id của từng dòng, đánh dấu khoảng 20% tập dữ liệu theo cách random
  + lôi nó vào test set của mình, sau này dựa vào các id đó chúng ta có thể lấy được các test set cũ mà không lo bị xáo trộn hay tập dữ liệu được update
  
 Tuy nhiên dữ liệu chúng ta lấy phải có độ trải đều chuẩn ví dụ như là bản ghi chúng ta có 1000 người 600 nam và 400 nữ thì giả dụ bộ test của chung ta lấy 100 người thì cũng phải có 60 nam và 40 nữ để đảm bảo độ chính xác. 

## Tìm hiểu data
Đầu tiền, sẽ tìm sự tương đồng giữa các giữa các cột dữ liệu với nhau
Có vài tip tìm hiểu được là
- Đưa nó lên dạng biểu đồ nhiệt chẳng hạn
```
housing.plot(kind="scatter", x="longitude", y="latitude", alpha=0.4,
s=housing["population"]/100, label="population", figsize=(10,7),
c="median_house_value", cmap=plt.get_cmap("jet"), colorbar=True,
)
plt.legend()
```
- Hoặc tìm sự tương tác hay `standard correlation coeffcient`
![image](https://user-images.githubusercontent.com/45547213/61842848-d7917280-aec3-11e9-8be2-f512dedab9a7.png)

nó sẽ chạy từ 1 đến -1. Nếu nó gần với 1 thì là có sự tương đồng cao và ngược lại với -1

1 cách nữa là dùng scatter matrix
```
from pandas.plotting import scatter_matrix
attributes = ["median_house_value", "median_income", "total_rooms",
              "housing_median_age"]
scatter_matrix(housing[attributes], figsize=(12, 8))
```


- Ngoài ra bạn có thể kết hợp các thuộc tính lại với nhau để có 1 thuộc tính hữu ích hơn

Chẳng hạn: thuộc tính tổng số phòng ngủ, tổng số phòng, tổng số hộ nhà sẽ không giá trị bằng tổng số phòng ngủ/ tổng số phòng và tổng số phòng ngủ/ tổng số hộ nhà

## Clean data
**Tip**: Thay vì làm bằng tay chúng ta nên viết function để dễ sử dụng lại, dễ chuyển đổi giữa các dataset

### Clean
- Đa phần các thuật toán ML không chạy được nếu có dữ liệu bị thiếu 
- Nên chúng ta cần sửa mấy cái này có 3 giải pháp:
  + xóa dòng có NA value đi
  + bỏ cột có NA value đi
  + set NA value = 0 hoặc = trung vị hoặc = trung bình
  
 Các method hỗ trợ là `dropna, drop, fillna`
 
sk-learn cũng có 1 cái làm mất na đi
```
from sklearn.impute import SimpleImputer
imputer = SimpleImputer(strategy="median")

imputer.fit(housing_num)
```

- Đa phần các thuật toán ML cũng ưu tiên làm việc với các con số chứ không phải text nên chúng ta phải chuyển về dạng số
```
from sklearn.preprocessing import LabelEncoder
encoder = LabelEncoder()
housing_cat = housing['ocean_proximity']
housing_cat_encoded = encoder.fit_transform(housing_cat)
housing_cat_encoded
```


### Scaling
Một trong những phép biến hình quan trọng nhất mà lập trình viên cần phải làm với dữ liệu của anh ta là features scaling - điều chỉnh độ giãn cách của thuộc tính. Ngoại trừ một vài trường hợp, thì các thuật toán ML sẽ không hoạt động tốt nếu các thuộc tính trong dữ liệu có độ giãn cách quá khác nhau. Đây chính là trường hợp mà dự án của chúng ta mắc phải : trong khi total_rooms có dải giá trị từ 6 tới 39320, thì median_income chỉ có giá trị từ 0 tới 15. Lưu ý rằng thường bạn sẽ không phải điều chính độ giãn cách của labels - target attribute.


Có hai cách phổ biến để làm cho các thuộc tính có được độ giãn cách như nhau : min-max scaling và standardization.

Đối với min-max scaling (nhiều người gọi nó là normalization) thì khá đơn giản: Các giá trị được điều chỉnh sao cho dải giá trị của nó nằm gọn trong đoạn $[0;1]$. Chúng ta làm điều này bằng cách trừ các giá trị cho min, sau đó chia giá trị vừa tính được cho (max - min). Thư viện Scikit-Learn cung cấp lớp MinMaxScaler cho mục đích này. Nó có một hyper-parameter feature_range để bạn thay đổi dải giá trị mặc định từ $[0;1]$ sang một dải khác nếu muốn.

Với standardization thì lại khá khác biệt. Nó làm cho dữ liệu của chúng ta có được cái gọi là phân phối chuẩn tắc - standard normal distribution. Trước tiên nó trừ các giá trị cho trung bình cộng của thuộc tính (nhờ đó mà thuộc tính sau khi được giãn cách sẽ có trung bình cộng là 0). Sau đó nó chia giá trị vừa tính được cho phương sai(bình phương độ lệch chuẩn) để thuộc tính cuối cùng có phương sai đơn vị: 1. Không giống với min-max scaling, standardization không điều chỉnh lại thuộc tính thành một dải giá trị cố định nào cả, điều này có thể sẽ gây vấn đề với một vài thuật toán (ví dụ : neural networks thường mong đợi các đầu vào có dải dữ liệu nằm trong $[0;1]$). Tuy nhiên, stardardization lại ít bị ảnh hưởng bởi ngoại lệ hơn. Ví dụ, giả sử rằng một quận có median_income = 100(do lỗi). Min-max scaling sẽ đánh sập các giá trị khác từ $[0;15]$ xuống còn $[0;0.15]$, trong khi đó standardization không bị ảnh hưởng quá nhiều. Scikit Learn cung cấp một lớp gọi là StandardScaler cho mục đích này.

## Data pipeline

Scikit-Learn cung cấp cho chúng ta lớp Pipeline để thao tác với các chuỗi transformers đó. Dưới đây là một ví dụ nho nhỏ về một Pipeline dùng cho các thuộc tính số học
```
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler

num_pipeline = Pipeline([
  ('imputer', Imputer(strategy='median')),
  ('attribs_adder', CombinedAttributesAdder()),
  ('std_scaler', StandardScaler())
])
housing_num_tr = num_pipeline.fit_transform(housing_num)
```
Ngoài ra chúng ta có thể kết hợp nhiều pipeline với nhau
```
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
num_pipeline = Pipeline([
('imputer', SimpleImputer(strategy="median")),
('attribs_adder', CombinedAttributesAdder()),
('std_scaler', StandardScaler()),
])
housing_num_tr = num_pipeline.fit_transform(housing_num)



from sklearn.compose import ColumnTransformer
num_attribs = list(housing_num)
cat_attribs = ["ocean_proximity"]
full_pipeline = ColumnTransformer([
                                ("num", num_pipeline, num_attribs),
                                ("cat", OneHotEncoder(), cat_attribs),
                                ])
housing_prepared = full_pipeline.fit_transform(housing)
```


## Train Models
- Bây giờ chọn 1 model rồi kiểm tra xem độ chính xác của nó như nào
```
housing_predictions = tree_reg.predict(housing_prepared)
tree_mse = mean_squared_error(housing_labels, housing_predictions)
tree_rmse = np.sqrt(tree_mse)
tree_rmse
```

```
def display_scores(scores):
... print("Scores:", scores)
... print("Mean:", scores.mean())
... print("Standard deviation:", scores.std())
```

```
from sklearn.model_selection import cross_val_score
scores = cross_val_score(tree_reg, housing_prepared, housing_labels,
scoring="neg_mean_squared_error", cv=10)
tree_rmse_scores = np.sqrt(-scores)
```

đôi khi cái model bị overfit nên chúng ta phải dùng validiation

### k-fold validiation
chia tập dữ liệu train ra thanh k lần rồi train k-1 cái còn lại tính score các thứ ra so thì sẽ chuẩn hơn 


```
from sklearn.model_selection import cross_val_score
scores = cross_val_score(tree_reg, housing_prepared, housing_labels,
scoring="neg_mean_squared_error", cv=10)
tree_rmse_scores = np.sqrt(-scores)
```

## Tuning Model
để chọn được các hyper parameter okke nhất chúng ta có 2 cách Grid search và Random search

- Với Grid Search, giả dụ giá trị của 2 parameter lần lượt từ 0-9. Grid Search sẽ lần lượt ghép từng giá trị của param 1 với param 2 để tính toán độ chính xác của model. Đảm bảo không bỏ sót cặp parameter nào.

Tính toán
```
from sklearn.model_selection import GridSearchCV
param_grid = [
{'n_estimators': [3, 10, 30], 'max_features': [2, 4, 6, 8]},
{'bootstrap': [False], 'n_estimators': [3, 10], 'max_features': [2, 3, 4]},
]
forest_reg = RandomForestRegressor()
grid_search = GridSearchCV(forest_reg, param_grid, cv=5,
scoring='neg_mean_squared_error',
return_train_score=True)
grid_search.fit(housing_prepared, housing_labels)
```

In ra cái param okke nhất
```
grid_search.best_params_
```

In ra cả list 
```
cvres = grid_search.cv_results_
for mean_score, params in zip(cvres["mean_test_score"], cvres["params"]):
  print(np.sqrt(-mean_score), params)
```

- Random search: đúng như tên gọi, từ những giá trị parameter bạn setting, Random Search sẽ chọn ngẫu nhiên các cặp parameter để tiến hành độ chính xác của model.

Sau đó đưa test set vào trong pipeline rồi chạy model thôi












