# DACON-이미지 색상화 및 손실 부분 복원 AI 경진대회
![image](https://github.com/user-attachments/assets/a6a29b5c-047c-4b78-a555-b0c25df79721)

## image inpainting
![image](https://github.com/user-attachments/assets/d6c3e9f8-7478-4477-a536-8926ab9a1606)

###### 출처: Jieun Lee, SeungWon Jung, Jonghwa Shim, Eenjun Hwang - [Super  Resolution-based  Robust  Image  Inpainting  for Large-scale  Missing  Regions]
##### Image-inpainting 기술이란 디지털 이미지 처리 기술의 일종으로, 손상된 이미지 영역을 복원하거나 삭제된 부분을 채워주는 기술이다. Image-inpainting은 예술, 의료, 보안 등 다양한 영역에서 활용되며, 기술 발전에 따라 더욱 자연스럽고 효율적인 복원이 가능해지고 있다
---
## 사용한 라이브러리 
<img src="https://img.shields.io/badge/python-3776AB?style=for-the-badge&logo=python&logoColor=white"> <img src="https://img.shields.io/badge/pytorch-EE4C2C?style=for-the-badge&logo=python&logoColor=white"> <img src="https://img.shields.io/badge/numpy-013243?style=for-the-badge&logo=python&logoColor=white"> <img src="https://img.shields.io/badge/tqdm-FFC107?style=for-the-badge&logo=python&logoColor=white">

---
## 모델 & 데이터 처리 접근 방향성
![image](https://github.com/user-attachments/assets/ed73797d-032d-41d3-b438-2cb681e39b6d)

##### Dataset는 위의 사진처럼 크게 3가지로 분류, test_gt가 없기 때문에 mask부분에 대한 학습이 가장 중요하다고 판단

-> 위의 내용을 토대로 다음과 같은 방법으로 진행
1. baseline (U-Net 기반의 Generator + PatchGAN 기반의 Discriminator)
2. Data augmentation
3. Mask extraction
4. U-Net(+EfficientNet-B5 backbone) + PatchGAN
5. Hyperparameter Tuning

**Hyperparameter Tuning을 진행했을 때 성능이 가장 높게 나와 ablation study 진행**

---
## 사용 모델
U-Net + PatchGAN

![스크린샷 2024-12-09 214630](https://github.com/user-attachments/assets/64d7b2fd-fec1-4f0a-be5c-7795652ca1c4)
![image](https://github.com/user-attachments/assets/5c665c1e-4a0f-439d-a23b-9ef1f3f242d5)

---
## Train
![image](https://github.com/user-attachments/assets/6033e4ed-ae77-44c2-93f6-540027276711)


Optimizer, LR, betas(모멘텀)를 각각 조절해보았을 때 Optimizer는 **AdamW**를 사용하고 LR은 **0.00003**, 그리고 Adam optimzier 중 이동 평균 계산에 사용되는 모멘텀은 **기본값(0.9,0.999)** 를 사용했을 때 결과값이 가장 좋았다



## 학습 Loss 그래프 시각화
![image](https://github.com/user-attachments/assets/48be336a-06e5-4eda-9be2-f8d1e47f5ea9)


---
## Result
![image](https://github.com/user-attachments/assets/48e7b2d4-91c0-4f89-8092-5b43d6483bf6)

![TEST_018](https://github.com/user-attachments/assets/5d804c3d-ae01-4e41-8263-828cf5821d38)


---
## Award
### 2024.12.09 기준 649명 중 public 7등 private 8등 ranking chart 5등
public
![image](https://github.com/user-attachments/assets/238d28a7-634d-49df-8943-4291dd96de30)

private
![image](https://github.com/user-attachments/assets/c8298d86-ecd3-4095-8d4b-4c4e470a004e)

ranking chart
![newplot](https://github.com/user-attachments/assets/2582ca81-f803-44b0-ae6e-ea7024f1c8bc)





