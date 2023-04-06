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
  * Đột biến
  ![image](https://user-images.githubusercontent.com/79850337/230320923-06b42bc0-c490-42c4-a22b-d95af338eede.png)
* Bước 4: Địng nghĩa hàm GA
  * Đặt kích thước quần thể là `size`
  * Thực hiện chọn ngẫu nhiên 4 cá thể trong quần thể, sau đấy chọn ngẫu nhiên cá thể tốt nhất làm `father1`. Tương tự thu được `father2`. Nếu xảy ra lai ghép thì thực hiện lai ghép trên 2 cá thể cha `father1`, `father2` để tạo 2 cá thể con, nếu xảy ra đột biến thì thực hiện đột biến trên 2 cá thể còn vừa được lai ghép ở trên. Nếu không xảy ra lai ghép thì tạo 2 cá thể con giống 2 cá thể `father1`, `father2` (**)
  * Lặp bước (**) `size/2` lần, ta thu được quần thể con có `size` cá thể
  * Sau bước trên ta thu được `quần thể con` có `size` cá thể và `quần thể cũ` có `size` cá thể. Ta lựa chọn các cá thể để tạo quần thể mới theo các bước như sau:
    * Chọn `2` cá thể tốt nhất trong `quần thể con` và `2` cá thể tốt nhất trong `quần thể cũ` thể thêm vào `quần thể mới`
    * Còn lại chọn ngẫu nhiên `size - 2 - 2` cá thể trong `size + size - 2 - 2` cá thể còn lại để thêm vào `quần thể mới`

## Thực thi giải thuật GA trên 30 seed (từ 0 -> 29) với các tham số: (tập dữ liệu `eli51`, kết quả tối ưu `fitness = 450`)
`Kích thước quần thể`: 100\
`Số thế hệ`: 500\
`Tỷ lệ lai ghép Pc`: 0.9\
`Tỷ lệ đột biến Pm`: 0.1
* Kết quả khi sử dụng toán tử lai ghép `một điểm cắt`:
  * 5 seed có best fitness thấp nhất:
  
    ![image](https://user-images.githubusercontent.com/79850337/230364832-7c36060f-f8cd-4727-9337-8bb94dee6fac.png)
  * Best fitness trên từng thế hệ của seed tốt nhất:
  ![image](https://user-images.githubusercontent.com/79850337/230364943-4c7d07f0-61a2-441f-b6b5-2f686ebaf81d.png)
  * Đường đi tốt nhất:
  
    ![image](https://user-images.githubusercontent.com/79850337/230364995-4899d4d5-4524-46f5-b519-b9dd88f5842c.png)
* Kết quả khi sử dụng toán tử lai ghép `hai điểm cắt`:
  * 5 seed có best fitness thấp nhất:
  
    ![image](https://user-images.githubusercontent.com/79850337/230365229-7f52f240-037b-4240-b0a4-df717040679a.png)
  * Best fitness trên từng thế hệ của seed tốt nhất:
  ![image](https://user-images.githubusercontent.com/79850337/230365280-35d17cb4-390e-46f7-8626-e8f4047c4e09.png)
  * Đường đi tốt nhất:
  
    ![image](https://user-images.githubusercontent.com/79850337/230365332-d111caa5-c3a5-4de0-a800-8cd39fa21274.png)
* So sánh:

![image](https://user-images.githubusercontent.com/79850337/230365369-c61a1d8e-582a-4931-bfd2-3fd084a41a01.png)

## Thực thi giải thuật GA với các tham số như trên và chỉ thay đổi từ `500 thế hệ` thành `1000 thế hệ`:
* Kết quả khi sử dụng toán tử lai ghép `một điểm cắt`:
  * 5 seed có best fitness tốt nhất:
    
    ![image](https://user-images.githubusercontent.com/79850337/230359922-df9af1fe-47d4-4751-87e7-0f1473f059fe.png)
  * Best fitness trên từng thế hệ của seed tốt nhất:
  ![image](https://user-images.githubusercontent.com/79850337/230360930-f8c4f4aa-7beb-40bb-954b-18719dae22f8.png)
  * Đường đi tốt nhất:
  
    ![image](https://user-images.githubusercontent.com/79850337/230361010-74276176-ae1d-45ae-85a6-510c3b34ad91.png)
* Kết quả khi sử dụng toán tử lai ghép `hai điểm cắt`:
  * 5 seed có best fitness thấp nhất:
    
    ![image](https://user-images.githubusercontent.com/79850337/230364195-f6e1a45e-a311-440a-857d-d0aad97b61fe.png)
  * Best fitness trên từng thế hệ của seed tốt nhất:
  ![image](https://user-images.githubusercontent.com/79850337/230364335-60705372-7a43-4355-ae1b-751af2f9c707.png)
  * Đường đi tốt nhất:
  
    ![image](https://user-images.githubusercontent.com/79850337/230364380-1500c937-d8da-4ae1-8477-83a6c2a7ffd7.png)
* So sánh:

![image](https://user-images.githubusercontent.com/79850337/230364447-47b764a3-f586-4795-a775-8d5e56613a9b.png)
## So sánh tổng thể
`500 generations`

|  | Single-point crossover | Multi-point crossover |
| ------------- | ------------- | ------------- |
| Best fitness  | 625.15 | 486.36 |
| Time taken(s)  | 3.15 | 3.57 |

`1000 generations`

|  | Single-point crossover | Multi-point crossover |
| ------------- | ------------- | ------------- |
| Best fitness  | 594.28 | 458.08 |
| Time taken(s)  | 6.33 | 7.28 |





