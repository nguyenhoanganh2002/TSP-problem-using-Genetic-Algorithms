# Sử dụng giải thuật di truyền (Genetic Algorithm) để giải bài toán Người du lịch (TSP)
* Đầu vào: Danh sách các thành phố cùng với toạ độ tương ứng của nó 

  ![image](https://user-images.githubusercontent.com/79850337/230314968-be70853d-f65e-4d5a-90b4-0d5db1736d7b.png)
* Đầu ra: Đường đi đi qua tất cả các thành phố đúng 1 lần có tổng chiều dài ngắn nhất (hình minh hoạ)
![image](https://user-images.githubusercontent.com/79850337/230316411-029edcf1-84a8-4962-8b60-19a384e79ad5.png)
## Các bước xây dựng giải thuật GA:
`Một cá thể (hay một lời giải chấp nhận được) là một danh sách có thứ tự các thành phố sẽ đi qua. Ví dụ: [3,7,1,5,8,6,2]`
* Bước 1: Đọc dữ liệu đầu vào và tạo `ma trận khoảng cách` giữa các cặp thành phố
* Bước 2: Định nghĩa hàm `fitness()` nhận đầu vào là một cá thể. Ở đây là hàm tính tổng khoảng cách khi đi thành phố đầu đến thành phố cuối và quay lại thành phố đầu
* Bước 3: Định nghĩa các toán tử lai ghép và đột biến
  * Lai ghép một điểm cắt (single-point crossover)
  ![image](https://user-images.githubusercontent.com/79850337/230320401-2b71240d-40a8-428d-b5bd-c38a10dfa221.png)
  * Lai ghép 2 điểm cắt ( multi-point crossover)
  ![image](https://user-images.githubusercontent.com/79850337/230320600-8b0a9974-64d8-4d67-bf58-30d7b0594968.png)
  * Lai ghép vòng ( cycle crossover)
  
    ![image](https://user-images.githubusercontent.com/79850337/230320777-aa7bb99c-e8c9-4126-9e47-e7db7c384b04.png)
  * Đột biến
  ![image](https://user-images.githubusercontent.com/79850337/230320923-06b42bc0-c490-42c4-a22b-d95af338eede.png)
* Bước 4: Địng nghĩa hàm GA
  * Đặt kích thước quần thể là `size`
  * Thực hiện chọn ngẫu nhiên 4 cá thể trong quần thể, sau đấy chọn ngẫu nhiên cá thể tốt nhất làm `father1`. Tương tự thu được `father2`. Nếu xảy ra lai ghép thì thực hiện lai ghép trên 2 cá thể cha `father1`, `father2` để tạo 2 cá thể con, nếu xảy ra đột biến thì thực hiện đột biến trên 2 cá thể còn vừa được lai ghép ở trên. Nếu không xảy ra lai ghép thì tạo 2 cá thể con giống 2 cá thể `father1`, `father2` (**)
  * Lặp bước (**) `size/2` lần, ta thu được quần thể con có `size` cá thể
  * Sau bước trên ta thu được `quần thể con` có `size` cá thể và `quần thể cũ` có `size` cá thể. Ta lựa chọn các cá thể để tạo quần thể mới theo các bước như sau:
    * Chọn `2` cá thể tốt nhất trong `quần thể con` và `2` cá thể tốt nhất trong `quần thể cũ` thể thêm vào `quần thể mới`
    * Còn lại chọn ngẫu nhiên `size - 2 - 2` cá thể trong `size + size - 2 - 2` cá thể còn lại để thêm vào `quần thể mới`

## Thực thi giải thuật GA với các tham số:
`Kích thước quần thể`: 100\
`Số thế hệ`: 500\
`Tỷ lệ lai ghép Pc`: 0.9\
`Tỷ lệ đột biến Pm`: 0.1
* Kết quả khi sử dụng toán tử lai ghép `một điểm cắt`

