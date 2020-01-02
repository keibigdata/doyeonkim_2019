# 딥러닝 기반 환경이슈 감성분류기 개발 : 기후변화 중심으로(Ⅱ)
  본 연구는 기후변화 주제의 SNS와 뉴스 댓글 데이터 기반 딥러닝을 이용한 감성분류기를 개발하는 연구입니다
  본 repository에서 제공하는 data 및 code에 대한 설명은 다음과 같습니다.
  
## 1_ 감성분류 학습 데이터
- 약 5만 건 단문 데이터 : 4개 채널(Facebook, Instagram, News_comment, Twitter)에서 본 연구에서 구축한 기후변화 사전을 이용하여 수집함
- 2개 감성 : 1. 긍정(황홀/기쁨, 기대/관심, 감탄/존경) 및 중립, 2. 부정(분노/짜증, 두려움/공포, 슬픔/수심)
- Windows 환경에서 학습 데이터 다운로드 시 이모지(Emoji)가 깨져보여 이모지를 한글로 변환함.
>  참고 : 이모지 포함된 학습데이터 등은 doyeonkim_2018 학습 데이터 자료 참고
![DIC](https://user-images.githubusercontent.com/29788540/71659713-e726b880-2d8b-11ea-9369-f9e8ec19b59a.png)

## 2_ Conv-BiLSTM 감성분류기 알고리즘 코드
 - 분석 순서 :
 ![PROCESS](https://user-images.githubusercontent.com/29788540/71659735-fdcd0f80-2d8b-11ea-8ecb-3c9741064f42.png)
 
> 1. 데이터 전처리(특수문자제거, 조사제거, 자모 분류, 음절 분류 등)
![TOKEN](https://user-images.githubusercontent.com/29788540/71659119-bfceec00-2d89-11ea-9be4-65dc42683e39.png)
> 2. 형태소 분석(Mecab, Twitter)
> 3. 4개 학습데이터 구축(1. Mecab 2. Twitter 3. 음절 4. 자모)
> 4. 4개 학습데이터기반의 Conv-BiLSTM 앙상블모델 구축
![MODEL](https://user-images.githubusercontent.com/29788540/71658976-2bfd2000-2d89-11ea-96ad-c6cf3eb3885b.png)
> 5. 성능평가(Accuracy, Precision, Recall, Fbeta, Ap score), Cutoff Selection Plot
![PERFORMANCE](https://user-images.githubusercontent.com/29788540/71659556-62d43580-2d8b-11ea-930f-349dea4a0ea9.png)
![AP](https://user-images.githubusercontent.com/29788540/71659703-dece7d80-2d8b-11ea-9415-7a5cce707b5e.png)

