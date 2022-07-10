# Hate_Detect_AMCNN
Attention기반 Multichannel CNN을 활용한 혐오 댓글 탐지기

### Data Crawling
네이버 영화 '평점'데이터 크롤링

* Original Dataset: <82년생 김지영>, <공작>, <남산의 부장들>, <국제시장> 등 혐오 발화가 빈번히 발생할 것으로 예측되는 영화 4편을 선정

  * 평점 1점 데이터 중 21% 무작위 추출하여 Train Set으로 활용
  
* Test set: <캡틴 마블>, <공조>, <택시운전사>: Train Set과 Cosine Similarity 높은 영화로 선정

### Labeling
* 혐오 유형 설정: '혐오/비혐오'로 1차 분류, 혐오 유형을 '성별/이념 및 지역/인간 존엄성'으로 2차 분류

  * 혐오의 기준은  [Youtube 증오 표현 정책](https://support.google.com/youtube/answer/2801939?hl=ko&ref_topic=9282436)을 참고함

### Transform
혐오 유형에 따라 KcBERT, KcELECTRA 중 Val loss 낮은 모델 채택

### Modeling
Based on [whjzsy/AMCNN](https://github.com/whjzsy/AMCNN)

1. Feature Channel
  : Embedding & Bi-LSTM
2. Attention Layer
  : Encoder-Decoder, Scalar Attention, Vector Attention
3. CNN Network
  : 2D Convolution, 2D Maxpooling, Anti-Overfitting (Batch Norm., Dropout)
4. Highway Network

### Results & Applications
Please check [Presentation Video](https://youtu.be/0KA7pYfUbbs)
