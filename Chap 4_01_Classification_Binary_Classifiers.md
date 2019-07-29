# Classification

**Định nghĩa**: 
- Classification thường thuộc nhóm học có giám sát (supervised learning), người ta cho máy học các tập training set với các label có sẵn 
trong tập training đó để máy sau này nhờ những kiến thức học được đó có thể tự động phân lớp được các dữ liệu đầu vào 
## Binary Classifiers
**Định nghĩa**: 
chỉ có 2 cái class thôi
### Confusion Matrix 
Để đo lường hiệu năng của classifier người ta thường dùng confusion matrix
**Nguyên lý**: Đếm số lần biến thuộc lớp A được phân loại thành biến của lớp B. Để tính toán Confusion Matrix bạn cần phải có 1 tập 
predictions để có thể so sánh với thực tế

Công thức tính độ chuẩn xác dựa trên confusion matrix
![image](https://user-images.githubusercontent.com/45547213/62018410-c064c480-b1e4-11e9-93b4-39d38bb2cd30.png)

Khi bạn muốn so sánh giữa các model với nhau, người ta sẽ so sánh F1 score(thực chất là recall và precision gộp lại)

![image](https://user-images.githubusercontent.com/45547213/62018931-f2772600-b1e6-11e9-8899-d4c38f8dd1ee.png)

**Lưu ý**: precision và recall là 2 đại lượng đối nghịch nhau không cùng tăng được 1 cái tăng thì 1 cái phải giảm và tùy vào mục đích
của project mà chúng ta sẽ hiểu chỉnh 

![image](https://user-images.githubusercontent.com/45547213/62019510-5e5a8e00-b1e9-11e9-83ce-feb6841d4c91.png)

### Cách set ngưỡng
sklearn không cho chúng ta set 1 cách trực tiếp nhưng chúng ta có thể thay vì gọi hàm `classifier’s
predict()`, chúng ta sẽ gọi `decision_function()` mà sẽ trả về score cho mỗi biến, rồi dự đoán trên những scores đấy với bất kì ngưỡng
nào bạn muốn
```
>>> y_scores = sgd_clf.decision_function([some_digit])
>>> y_scores
array([2412.53175101])
>>> threshold = 0
>>> y_some_digit_pred = (y_scores > threshold)
array([ True])
>>> threshold = 8000
>>> y_some_digit_pred = (y_scores > threshold)
>>> y_some_digit_pred
array([ False])
```
Với việc set threshold lên 8000 thì recall đã giảm đồng thời precision tăng

- Bây giờ chúng ta sẽ lấy score của tất cả các instance bằng hàm cross_val_predict nhưng method sẽ là decision_function
```
y_scores = cross_val_predict(sgd_clf, X_train, y_train_5, cv=3,
method="decision_function")
```

### ROC curve
**Định nghĩa**: đường cong ROC (receiver operating characteristic ) cũng là 1 common tool cho binary classifier. Nó khá giống với 
recall/precision curve. ROC curve là biểu đồ so sánh giữa `True Positive Rate` với `False Positive Rate` ( là các biến thực chất là sai 
nhưng lại được phân loại là đúng). FPR = 1- TNR( True Neagative Rate là các biến được phân loại đúng vào negative)
```
from sklearn.metrics import roc_curve

fpr, tpr, thresholds = roc_curve(y_train_5, y_scores)

def plot_roc_curve(fpr, tpr, label=None):
    plt.plot(fpr, tpr, linewidth=2, label=label)
    plt.plot([0, 1], [0, 1], 'k--') # dashed diagonal
    # Add axis labels and grid
plot_roc_curve(fpr, tpr)
plt.show()
```

- Công thức 
![image](https://user-images.githubusercontent.com/45547213/62029269-5cee8d00-b20c-11e9-9066-db8e7ba82a08.png)

![image](https://user-images.githubusercontent.com/45547213/62029365-97f0c080-b20c-11e9-949d-c5d3cc14bee0.png)












