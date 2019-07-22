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
Reinforcement Learning is a very different beast. The learning system, called an agent in this context, can observe the environment, 
select and perform actions, and get rewards in return (or penalties in the form of negative rewards, as in Figure 1-12).
It must then learn by itself what is the best strategy, called a policy, to get the most reward over time. 
A policy defines what action the agent should choose when it is in a given situation.

Reinforcement Learning là một hệ thống rất khác. The learning system, được gọi là một agent trong bối cảnh này, 
có thể quan sát môi trường, lựa chọn và thực hiện các hành động và nhận lại phần thưởng (hoặc hình phạt dưới dạng phần thưởng tiêu cực, 
như trong Hình 1-12). Sau đó, nó phải tự học chiến lược tốt nhất, được gọi là chính sách để nhận phần thưởng nhiều nhất theo thời gian.
Chính sách xác định hành động nào mà tác nhân nên chọn khi nó ở trong một tình huống nhất định.

















