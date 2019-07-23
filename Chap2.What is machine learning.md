## What is machine learning?
Machine learning là 1 ngành khoa học (cũng là nghệ thuật) của lập trình máy tính để máy tính có thể học từ dữ liệu

Ví dụ nhé: Bộ lọc mail rác là 1 chương trình machine learning.

Các ví dụ mà hệ thống dùng để học là training set(tập training)

Mỗi 1 ví dụ là 1 training instance(biến training)


## Tại sao cần machine learning
- Các vấn đề mà các giải pháp hiện tại yêu cầu rất nhiều điều chỉnh bằng tay hoặc danh sách dài các quy tắc: 
một thuật toán Machine Learning thường có thể đơn giản code và hiệu năng mượt mà hơn.
- Các vấn đề phức tạp mà hoàn toàn không có giải pháp tốt bằng cách sử dụng phương pháp truyền thống: 
các kỹ thuật Machine Learning có thể tìm ra giải pháp.
- Môi trường dao động: một hệ thống Machine Learning có thể thích ứng với dữ liệu mới.
- Hiểu biết sâu sắc về các vấn đề phức tạp và lượng dữ liệu lớn.

## Các loại hệ thống Machine Learning
- Hệ thống có được đào tạo với sự giám sát của con người hay không (giám sát, không giám sát, bán chuyên nghiệp và học tập củng cố)
- Hệ thống có thể học tăng dần hay không (học trực tuyến so với học theo đợt)
- Hệ thống làm việc bằng cách đơn giản so sánh các điểm dữ liệu mới với các điểm dữ liệu đã biết hoặc
thay vào đó phát hiện các mẫu trong dữ liệu đào tạo và xây dựng mô hình dự đoán, 
giống như các nhà khoa học thực hiện (học tập dựa trên mô hình so với mô hình)

## Supervised/Unsupervised Learning
Hệ thống Machine Learning có thể được phân loại theo số lượng và loại giám sát họ nhận được trong quá trình đào tạo.
Có bốn loại chính: supervised learning, unsupervised learning, semisupervised learning, and Reinforcement Learning..

### Supervised Learning
Trong supervised learning, training data bạn đưa cho thuật toán bao gồm cả cách xử lí được gọi là labels

![image](https://user-images.githubusercontent.com/45547213/61622342-cc113200-ac9e-11e9-8ca3-460841ebe967.png)

1 task cơ bản của supervised learning là phân loại như bộ lọc mail rác

1 task khác là dự đoán, người ta cho các thuộc tính sau đó cho nó học lần sau nó tự biết  

![image](https://user-images.githubusercontent.com/45547213/61622717-899c2500-ac9f-11e9-831f-31bc736e68c3.png)


### Unsupervised learning
Học không giám sát là training data ko có label

Các kiểu 
- Phân cụm
- Mô hình hóa dữ liệu
- Giảm chiều dữ liệu
- Phát hiện sự bất thường

### Semisupervised learning
trong 1 tập dữ liệu có cái được gán nhãn rồi có cái chưa được gán nhãn nó gọi là

### Reinforcement Learning
Reinforcement Learning là một hệ thống rất khác. The learning system, được gọi là một agent trong bối cảnh này, 
có thể quan sát môi trường, lựa chọn và thực hiện các hành động và nhận lại phần thưởng (hoặc hình phạt dưới dạng phần thưởng tiêu cực, 
như trong Hình 1-12). Sau đó, nó phải tự học chiến lược tốt nhất, được gọi là chính sách để nhận phần thưởng nhiều nhất theo thời gian.
Chính sách xác định hành động nào mà tác nhân nên chọn khi nó ở trong một tình huống nhất định.

![image](https://user-images.githubusercontent.com/45547213/61697095-c7ad4d80-ad60-11e9-8e01-c8a6f78f7fd7.png)

Ví dụ:
Robot học cách đi bằng Reinforcement Learning

## Batch and Online Learning
Một tiêu chí khác được sử dụng để phân loại các hệ thống Machine Learning là liệu hệ thống có thể học tăng dần từ một luồng dữ liệu đến hay không.

### Batch learning
Trong Batch learning, hệ thống không có khả năng học tăng dần: nó phải được đào tạo bằng cách sử dụng tất cả các dữ liệu có sẵn. Điều này thường sẽ tốn rất nhiều thời gian và tài nguyên máy tính, vì vậy nó thường được thực hiện offline. Đầu tiên hệ thống được training, và sau đó nó được đưa vào  chạy mà không cần học nữa; nó chỉ áp dụng những gì nó đã học. Điều này được gọi là offline learning.

Nếu bạn muốn nó học cái mới thì phải update các kiểu việc update đơn giản nhưng bạn sẽ tốn nhiều tài nguyên máy tính và thời gian và 
với số lượng lớn về data thì cái này chịu =)))

### Online learning
Trong Online learning, bạn huấn luyện hệ thống tăng dần bằng cách cung cấp cho nó các trường hợp dữ liệu theo tuần tự, theo từng cá nhân hoặc theo nhóm nhỏ gọi là các đợt nhỏ. Mỗi bước học nhanh và rẻ, vì vậy hệ thống có thể tìm hiểu về dữ liệu mới một cách nhanh chóng khi nó đến

- Tốt cho
  + Đối đầu với dòng dữ liệu liên tục
  + tiết kiệm tài nguyên máy tính
  + có thể học 1 lượng dữ liệu lớn mà vượt quá cả bố nhớ của máy tính
 - Lưu ý
 
  + Có 1 cái gọi là learning rate nó cho phép ta điều chỉnh độ nhạy cảm của máy tính với thông tin mới, nếu nó học nhanh thì nó quên dữ liệu cũ cũng nhanh
  + Và cái cuối nếu nó bị học nhầm dữ liệu xấu thì hiệu năng của nó sẽ giảm nên chúng ta cần giám sát kĩ xem những gì nó đang học có okke ko
  
## Instance-Based Versus Model-Based Learning
Một cách nữa để phân loại các hệ thống Machine Learning là cách chúng "generalize"(khái quát hóa). Hầu hết các nhiệm vụ Machine Learning là về việc đưa ra dự đoán. Điều này có nghĩa là với một số ví dụ đào tạo, hệ thống cần có khả năng khái quát hóa cho các ví dụ mà nó chưa từng thấy trước đây. Có một thước đo hiệu suất tốt cho training data là tốt, nhưng không đủ; mục tiêu thực sự là thực hiện tốt trong các trường hợp mới.

### Instance-based learning
hệ thống học thuộc lòng các ví dụ, sau đó khái quát hóa cho các trường hợp mới bằng cách so sánh chúng với các ví dụ đã học (hoặc một tập hợp con của chúng), sử dụng thước đo tương tự. Ví dụ, instance mới sẽ được phân loại thành một hình tam giác vì phần lớn các thể hiện tương tự nhất thuộc về lớp đó.

### Model base learning
- Bạn nghiên cứu dữ liệu.
• Bạn chọn một mô hình.
• Bạn đào tạo nó với dữ liệu đào tạo (nghĩa là, thuật toán học tập  tìm mô hình có các giá trị tham số có hàm cost nhỏ nhất).
• Cuối cùng, bạn đã áp dụng mô hình để đưa ra dự đoán về các trường hợp mới (cái này được gọi là
suy luận), hy vọng rằng mô hình này sẽ khái quát tốt.

## Các thách thức của machine learning
Nói tóm lại, vì nhiệm vụ chính của bạn là chọn một thuật toán và huấn luyện nó trên một số dữ liệu, hai điều có thể sai là thuật toán tồi, dữ liệu không đúng, chúng ta sẽ bắt đầu dữ liệu xấu. 








