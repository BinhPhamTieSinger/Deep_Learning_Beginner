# <font color='red'>COMPUTER VISION WITH DEEP LEARNING</font>

# <font color='blue'>Face Recognition with GhostFaceNet</font>

- **Dataset:** Sử dụng tập data_new.zip chứa 864 hình gương mặt của 199 người (identity từ 0 đến 198) cùng file data.csv chứa tên ảnh và nhãn identity.

- **Yêu cầu chính:**
  
  - Sử dụng kiến trúc GhostFaceNet (2023) với pretrained weight để xây dựng mô hình nhận diện khuôn mặt, đạt độ chính xác >98% (đánh giá qua Accuracy, TPR, FPR, ROC, v.v.).
  
  - **Mô phỏng đăng ký user mới:**
    
    - Tính Mean Face Embedding cho mỗi identity dựa trên các ảnh hiện có (ví dụ: 100 vector đại diện cho 100 identity).
    
    - Giả sử user mới submit 2 ảnh chân dung cùng một người, từ đó khởi tạo vector đại diện và add thông tin (ID, filenames) vào bộ data sẵn có.
  
  - **Mô phỏng login:**
    
    - Người dùng submit 1 ảnh (khác với 2 ảnh đăng ký) thuộc cùng identity.
    
    - Xác định ID của ảnh đó và visualize các ảnh chân dung tương ứng của identity được nhận diện.

- **Bài giải:**

Notebook link: [Face Recognition With GhostFaceNet](https://colab.research.google.com/drive/1FSOmuh382_pZpMdwLrdKVBxFyeY3948p?usp=sharing)

Kết quả mô hình GhostFaceNet (2023) `GhostFaceNet_W1.3_S1_ArcFace.h5`:

|     | 1e-06    | 1e-05    | 0.0001   | 0.001    | 0.01     | 0.1      |
|:--- | --------:| --------:| --------:| --------:| --------:| --------:|
| TPR | 0.967593 | 0.974537 | 0.989583 | 0.996528 | 0.997685 | 0.998843 |

![](D:\AI_Learning\Deep_Learning\Q4\Images\Evaluation.png)

Ảnh đăng nhập vào hệ thống:

![](Images\Portrait_1.jpg)

![](Images\portrait_2.jpeg)

Ảnh để check đăng nhập:

![](Images\portrait_3.jpeg)

Kết quả: Hợp lệ với distance nhỏ nhất

```python
distances[0] = array([0.80291826], dtype=float32)
```
