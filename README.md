# cv_1) 특징추출

### 1-1) 이미지특징 추출
##### 이미지에서 특징추출 (SIFT descriptor) 
##### PCA로 정규화된 특징벡터 생성 (features)

### 1-2) 이미지특징 인코딩(히스토그램화) 
##### 특징인코딩 (codebook.encode(features))
##### 인코딩된 특징벡터 (train_encoded_features) 

### 1-3) 인코딩된벡터로 SVM학습, Confusion Matrix생성
##### 인코딩된특징으로 X_train, Y_train생성후 
##### SVM학습 (model.fit(X_train, Y_train))
##### 모델예측값생성 (y_pred = mode.predict(X_test))
##### Confusion Matrix생성 (Confusion_Matrix = confusion_matrix(y_test, y_pred))
 
<br><br> 
# cv_2) MLP, CNN 구현

### 2-1 ) EuroSAT 데이터셋전처리 
##### - EuroSAT데이터셋 다운로드, 전처리
##### - train, val, test 데이터셋으로 분할 

### 2-2 ) MLP모델구현 
##### - 멀티레이어 정의
##### - Activation(비선형성추가), Dropout(과적합방지) 사용
 
### 2-3 ) CNN모델구현
##### 컨볼루션레이어 정의 (특징추출)
##### - Activation(ReLU 활성화함수), Pooling사용
##### Fully Connected레이어 정의 (최종출력생성) 
##### - Activation, Dropout 사용  

### 2-4 ) MLP,CNN 모델학습, 결과분석
##### - 손실함수 (nn.CrossEntropy) 최소화방향으로 
##### - Adam옵티마이저 적용하여 모델업데이트  
##### - 테스트데이터셋으로 성능평가하여 CNN성능이 더좋음을확인  
##### - (MLP:1차원벡터변환으로 공간구조손실 / CNN:공간구조유지한 convolution연산구조)

<br><br>  
# cv_3) Segmentation Test

### 3-1 ) Segmentation 모델선택  , Segmentation테스트 
##### - 모델 : COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x.yaml  
##### - 풍선이미지 데이터셋 다운로드 / 전처리 (def get_balloon_dicts)
##### - 풍선이미지 데이터셋을 모델에 적용한 segmentation결과확인  

### 3-2 ) Segmentation 모델 finetuning 
##### - 파인튜닝 config 설정 
##### - 모델 디렉토리생성
##### - 모델 학습 (trainer = DefaultTrainer(cfg))

### 3-3 ) 모델 성능평가 (COCOEvaluator사용, AP, AR측정)
##### - 파인튜닝된모델 vs 사전학습모델

