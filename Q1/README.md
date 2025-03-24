# <font color='red'>COMPUTER VISION WITH DEEP LEARNING</font>

# <font color='blue'>Image Classification with Transfer Learning</font>

Trong bài toán này, chúng ta sẽ sử dụng kỹ thuật transfer learning để xây dựng mô hình nhận diện 5 loại hoa dựa trên dataset từ Kaggle ([Flowers Recognition | Kaggle](https://www.kaggle.com/datasets/alxmamaev/flowers-recognition)).

**Yêu cầu:**

- Chia dữ liệu thành 3 tập: train/val/test theo tỉ lệ 56/14/30.
- Huấn luyện mô hình với accuracy trên tập test > 90%.
- Thử nghiệm ít nhất 2 trong số 4 phương pháp sau:
  - Test Time Augmentation
  - Label Smoothing Loss (sử dụng code mẫu đã cho)
  - Sử dụng Learning Rate Scheduler
  - Thay đổi Optimizer (bất kỳ)

Sau khi huấn luyện, chúng ta sẽ report kết quả theo bảng và đưa ra nhận xét về hiệu quả của các kỹ thuật đã chọn.

**Bài giải:**

Notebook link: [Transfer Learning Flower Recognition Advanced | Kaggle](https://www.kaggle.com/code/tiesinger/transfer-learning-flower-recognition-advanced)

Các mô hình được thử nghiệm:

```python
models_exp = {
    "EfficientNet_b4": init_model(models.efficientnet_b4(pretrained=True), device),
}

optimizers = {
    "Adam": torch.optim.Adam(model.parameters(), lr=0.0001, betas=(0.9, 0.999), eps=1e-08, weight_decay=0),
    "AdamW": optim.AdamW(model.parameters(), lr=0.001, weight_decay=1e-4),
    "Lion": Lion(model.parameters(), lr=0.001, weight_decay=1e-4),
}

schedulers = {
    "ReduceLROnPlateau": ReduceLROnPlateau(optimizers["AdamW"], mode="min", patience=2, factor=0.5, verbose=True),
    "CosineAnnealingLR": CosineAnnealingLR(optimizers["AdamW"], T_max=10),
    "CosineAnnealingWarmRestarts": CosineAnnealingWarmRestarts(optimizers["AdamW"], T_0=5, T_mult=2)
}
```

Mô hình cho được kết quả tốt nhất:
```tex
Model: EfficientNet_b4; Optimizer: AdamW; Scheduler: CossineAnnealingWarmRestarts
```

Có sử dụng `criterion = LabelSmoothingLoss` và `Test Time Augmentation (TTA)`

Kết quả các mô hình:

1. Mô hình được train với bộ weights được freeze

```tex
Test Loss: 0.2730, Test Accuracy: 0.8603
Classification Report:
              precision    recall  f1-score   support

           0       0.91      0.84      0.88       229
           1       0.86      0.91      0.88       316
           2       0.90      0.80      0.85       235
           3       0.83      0.85      0.84       220
           4       0.82      0.88      0.85       296

    accuracy                           0.86      1296
   macro avg       0.86      0.86      0.86      1296
weighted avg       0.86      0.86      0.86      1296
```

2. Mô hình tiếp tục train nhưng được thay đổi bộ weights

```tex
Test Loss: 0.1316, Test Accuracy: 0.9375
Classification Report:
              precision    recall  f1-score   support

           0       0.97      0.94      0.96       229
           1       0.92      0.95      0.94       316
           2       0.96      0.92      0.94       235
           3       0.97      0.91      0.94       220
           4       0.90      0.95      0.92       296

    accuracy                           0.94      1296
   macro avg       0.94      0.94      0.94      1296
weighted avg       0.94      0.94      0.94      1296
```

3. Mô hình có kết hợp với `Test Time Augmentation (TTA)`

```tex
TTA Test Loss: 0.1415, TTA Test Accuracy: 0.9329
TTA Classification Report:
              precision    recall  f1-score   support

           0       0.92      0.94      0.93       229
           1       0.92      0.96      0.94       316
           2       0.93      0.94      0.93       235
           3       0.97      0.91      0.94       220
           4       0.93      0.91      0.92       296

    accuracy                           0.93      1296
   macro avg       0.93      0.93      0.93      1296
weighted avg       0.93      0.93      0.93      1296
```
