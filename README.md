# Naive Bayes lassifcation
## 1. Khái niệm
Lý thuyết về Bayes thì có lẽ không còn quá xa lạ với chúng ta nữa rồi. Nó chính là sự liên hệ giữa các xác suất có điều kiện. Điều đó gợi ý cho chúng ta rằng chúng ta có thể tính toán một xác suất chưa biết dựa vào các xác suất có điều kiện khác. Thuật toán Naive Bayes cũng dựa trên việc tính toán các xác suất có điều kiện đó.

Naive Bayes Classification (NBC) là một thuật toán phân loại dựa trên tính toán xác suất áp dụng định lý Bayes. Thuật toán này thuộc nhóm Supervised Learning (Học có giám sát).

Theo định lý Bayes, ta có công thức tính xác suất như sau:

![image](https://user-images.githubusercontent.com/64195026/138584852-8edc0903-38cc-40ae-ac83-f48285d328d4.png)

Do đó ta có:

![image](https://user-images.githubusercontent.com/64195026/138584857-e88cb726-add6-4ab9-ac42-43bc4bab27ab.png)

Trên thực tế thì ít khi tìm được dữ liệu mà các thành phần là hoàn toàn độc lập với nhau. Tuy nhiên giả thiết này giúp cách tính toán trở nên đơn giản, training data nhanh, đem lại hiệu quả bất ngờ với các lớp bài toán nhất định
Cách xác định các thành phần (class) của dữ liệu dựa trên giả thiết này có tên là Naive Bayes Classifier

## 2. Mô hình thuật toán Navie Bayes
Một trong các bài toán nổi tiếng hiệu quả khi sử dụng NBC là bài toán phân loại text

Trong bài toán này, mỗi văn bản được thể hiện thành dạng bag of words, hiểu nôm na là thể hiện xem có bao nhiêu từ xuất hiện và tần suất xuất hiện trong văn bản, nhưng bỏ qua thứ tự các từ

Có 2 mô hình thuật toán Naive Bayes thường sử dụng là: mô hình Bernoulli và mô hình Multinomial. Trong bài toán này ta chỉ tìm hiểu mô hình Multinomial

## 3. Mô hình Multinomial
Mô hình này chủ yếu được sử dụng trong phân loại văn bản mà feature vectors được tính bằng Bags of Words. Lúc này, mỗi văn bản được biểu diễn bởi một vector có độ dài d chính là số từ trong từ điển. Giá trị của thành phần thứ i trong mỗi vector chính là số lần từ thứ i xuất hiện trong văn bản đó.

Ta tính xác suất từ xuất hiện trong văn bản P(xi∣y) như sau

![image](https://user-images.githubusercontent.com/64195026/138584866-ec219cf2-be2d-4315-940f-560e99d9f01d.png)

Trong đó:
+ Ni là tổng số lần từ xi xuất hiện trong văn bản.
+ Nc là tổng số lần từ của tất cả các từ x1,…xn xuất hiện trong văn bản.
+ Công thức trên có hạn chế là khi từ xi không xuất hiện lần nào trong văn bản, ta sẽ có Ni=0. Điều này làm cho P(xi∣y)=0
+ Để khắc phục vấn đề này, người ta sử dụng kỹ thuật gọi là Laplace Smoothing bằng cách cộng thêm vào cả tử và mẫu để giá trị luôn khác 0


![image](https://user-images.githubusercontent.com/64195026/138584921-218189bd-7a61-4dc9-8e8f-c055236d2254.png)

Trong đó:
+ α thường là số dương, bằng 1.
+ dα được cộng vào mẫu để đảm bảo ∑i=1dP(xi∣y)=1

## 4. Ví dụ: Bài toán phân loại email
+ Ta có bộ training data gồm E1, E2, E3. Cần phân loại E4
+ Nhãn N là thư not spam, còn S là thư spam
+ Bảng từ vựng: [w1,w2,w3,w4,w5,w6,w7].
+ Số lần xuất hiện của từng từ trong từng email tương ứng với bảng

![image](https://user-images.githubusercontent.com/64195026/138584948-104aae7a-4e76-4254-813d-1acac918e93a.png)


### Giải bài toán bằng Python:

### 1. Import thư viện cần thiết

![image](https://user-images.githubusercontent.com/64195026/138584976-3c290952-8435-41e4-8e8e-0868388dc525.png)

### 2. Khai báo dữ liệu training và nhãn

### ![image](https://user-images.githubusercontent.com/64195026/138584988-ab69910e-3678-4863-8887-2812de577a27.png)

### 3. Khai báo dữ liệu tập test

![image](https://user-images.githubusercontent.com/64195026/138584998-7f44606b-768a-459d-9175-74bb0734ae69.png)

### 4. Dán nhãn dữ liệu cho máy học

![image](https://user-images.githubusercontent.com/64195026/138585009-84684615-14c6-46d9-a7b2-5b5d738ae43a.png)


### 5. Cho máy predict tập test

![image](https://user-images.githubusercontent.com/64195026/138585057-8726f63b-3a79-4d80-94f5-e355049d8e28.png)

### 6. Kết quả

![image](https://user-images.githubusercontent.com/64195026/138585073-755fe918-7839-4f6f-89d4-dbf73e88cdd0.png)


