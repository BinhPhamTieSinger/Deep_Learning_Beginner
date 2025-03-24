# <font color=red>COMPUTER VISION WITH DEEP LEARNING</font>

# <font color=blue>Traffic Sign Detection with YOLOv11</font>

- **Dataset:** Sử dụng tập dữ liệu nhận diện biển báo giao thông từ Kaggle (YOLO format).

- **Yêu cầu chính:**
  
  - Chuyển đổi định dạng dữ liệu cho phù hợp với cấu trúc của mô hình YOLOv11.
  
  - Chia tập train ban đầu thành 2 phần: train official và validation.
  
  - Xây dựng và huấn luyện mô hình YOLOv11, tuning trên tập validation.
  
  - Visualize kết quả dự đoán (bounding box) trên 8 mẫu của tập test.
  
  - Đánh giá performance trên tập test (mAP @ 50 cho các nhãn) và nhận xét kết quả.

- **Bài giải:**

Notebook link: [Traffic_Sign_Detection_With_Yolo | Kaggle](https://www.kaggle.com/code/tiesinger/traffic-sign-detection-with-yolo)

1. Chia dữ liệu thành các tập train, valid, test và copy file ảnh, nhãn.

2. Tạo file YAML cấu hình dataset.

3. Huấn luyện mô hình YOLO (sử dụng YOLOv11 medium).

4. Visualize dự đoán trên 8 ảnh mẫu.

5. Đánh giá performance trên tập test.

Kết quả mô hình trên tập test:

| Class       | Images | Instances | Box(P | R     | mAP50 | mAP50-95) |
| ----------- | ------ | --------- | ----- | ----- | ----- | --------- |
| all         | 224    | 386       | 0.984 | 0.937 | 0.971 | 0.835     |
| prohibitory | 119    | 173       | 0.983 | 0.976 | 0.993 | 0.865     |
| danger      | 64     | 81        | 0.997 | 0.975 | 0.988 | 0.864     |
| mandatory   | 43     | 51        | 0.968 | 0.902 | 0.944 | 0.796     |
| other       | 61     | 81        | 0.986 | 0.896 | 0.959 | 0.814     |
