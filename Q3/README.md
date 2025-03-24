# <font color=red>COMPUTER VISION WITH DEEP LEARNING</font>

# <font color=blue>Pix2Pix with Generative AI (GAN)</font>

- **Dataset:** Sử dụng tập dữ liệu pix2pix/cityscapes từ Kaggle.

- **Yêu cầu chính:**
  
  - Áp dụng kiến thức về các mô hình GAN hoặc Diffusion.
  
  - Phát triển một mô hình GAN có khả năng tạo ra ảnh shoes từ ảnh edge.
  
  - Visualize và đánh giá kết quả tạo ảnh (so sánh đầu ra với hình mẫu mong muốn).

- **Bài giải:**

Notebook link: [Generative_AI | Kaggle](https://www.kaggle.com/code/tiesinger/generative-ai)

1. Định nghĩa Dataset cho Pix2Pix (Edges2Shoes)

2. Định nghĩa kiến trúc Generator (U-Net) và Discriminator (PatchGAN)

3. Định nghĩa Loss và Optimizer, Training Loop

4. Visualize kết quả trên tập Validation

Kết quả mô hình:

![](https://www.kaggleusercontent.com/kf/229325498/eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0JDLUhTMjU2In0..dg827FwyBhF0A2jobJRWQw.FhMZuO7hHLmqPl95kp8OEKMBOkDy4uHMZuA0dTds13VoU_nQVTcr1EBc7Vr9hF_ckQq15OQrUkRYp2U8gUmyj6Z5gqddKEDbiJerf5BcRYkxV18kph-aUxt6iscWtlQ7p6z5acJ7OPVfZuhVXTEmioZwcphZSIyZDN5EQ5ivivgTmyporoKfpaFGn7cextTstefCZhd4fdIBTyFDkz2zi9UA6dshxX41F14mtCaT3fxDZVn9Nw6TiX8CetIFfbzN1iTVs35B-SggB3bWLahKTS5aa9AkprLPP60wE1fhLH_zIHMneHRYrgOmPlXMEA-NBztR9CM4L9SHicKid78MjvOtTpaSdQpbncTDmqWvjAhcWojEcQ4oWsJzV5JLVy578JpZQnnWu_ZuMSFqhktg-yhbJQOfkCyQjzY4zaC6P5Sh9_JXNXP9LG4zWwC-pvwY96a_hZxJk8t2mOyXzVZfVjxrggrEG8O7Tz-8ZcXRp0Gjk3EqQ8wyORywslJ81YWBp88vhV9xcfrAwPMrSfNWNLL1E9RBZHnaDWRC68NjM22i2Slb_pxmPyDrhyw2aSrDoPL8TQMezP1XwcnMFABWpU1Gq_NJF3dcuagWlBCtZpBRL00RZvhnIIL9eh9BZoPs.2qjm3zOT3d7nUx1Vuri43Q/__results___files/__results___12_0.png)
