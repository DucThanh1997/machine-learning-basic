# Multi classifier class
## Định nghĩa:
Trước chỉ phân biệt 2 class thôi bây giờ phân biệt nhiều class, thì có nhiều thuật toán hỗ trợ cái này
(Random Forest classifiers or naive Bayes classifiers). Ngoài ra còn vài chiến thuật cho phép chúng ta từ binary phân biệt thành multi

- build 10 cái binary cho từng con số 
  + 0 và phần còn lại
  + 1 và phần còn lại
  + 2 và phần còn lại
  + 3 và phần còn lại
  + 4 và phần còn lại
  + 5 và phần còn lại
  + ....
Cái nào có score cao nhất thì là chính nó đây là One vs all (OvA)

- build 45 cái binary 
  + 1 với 2
  + 1 với 3
  + 1 với 4
  + 1 với 5
  + 1 với 6
  + 2 với 3
  + 2 với 4
  + 2 với 5
  + 2 với 6
  ......
Đây là one vs one cái nào có nhiều score nhất thì okke

# Multilabel
giống kiểu nhận diện khuôn mặt con người ấy mặt người có nhiều điểm mắt mũi mồm các kiểu, nó là 1 set label tên của nó là Thành,
1 set label khác là Cương, xong nhận diện vừa vừa ra là chuẩn

- Thuật toán đại diện K-neighbour
```
from sklearn.neighbors import KNeighborsClassifier
y_train_large = (y_train >= 7)
y_train_odd = (y_train % 2 == 1)
y_multilabel = np.c_[y_train_large, y_train_odd]
knn_clf = KNeighborsClassifier()
knn_clf.fit(X_train, y_multilabel)
```

##
**Định nghĩa**:
Nó chỉ đơn giản là một khái quát của phân loại đa nhãn trong đó mỗi nhãn có thể là đa lớp 
(nghĩa là, nó có thể có nhiều hơn hai giá trị có thể).

