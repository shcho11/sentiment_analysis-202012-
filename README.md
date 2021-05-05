# sentiment_analysis
한글 / 영어 감정분석기 시험
1. text classification
  - word tokenization, stemming, lemmatization, stopword deletion 등 실습
  - 한글 : KoNLPy, 영어 : nltk 사용

2. Keras
  * Keras 활용
   - 입력 텐서의 타겟텐서로 이루어진 훈련 데이터를 정의
   - 입력과 타겟을 mapping하는 층(layer)로 이루어진 모델 (혹은 네트워크)를 정의
   - 손실함수(loss function), 옵티마이저(Optimizer), 모니터링을 하기 위한 측정 지표를 선택, 학습과정을 설정.
   - 훈련 데이터에 대해 모델의 fit() 메서드를 반복적으로 호출, 훈련을 시작.
  * 리스트를 텐서로 바꿔줘야 하는데, 2가지 방법 있음
   - 같은 길이가 되도록 List에 padding을 추가, (samples,sequence_length)크기의 정수 텐서로 변환. 그 다음 이 정수텐서를 embedding layer로 사용.
   - List를 One-hot Encoding하여 0과 1의 벡터로 변환
  * 층을 깊게 만드는 장점 살리기 위해 비선형성 또는 활성화함수 추가해야 함. 주로 relu많이 사용.
  
3. CNN 이용한 감정분석
  - padding, pooling하여 분석 진행

!! 2와 3은 기존 깃허브 코딩 참고 <br>
   https://github.com/Parkchanjun/KU-NLP-2020-1.git <br>
   https://github.com/shna83/-DFE610-NLP-sentimental-analysis-.git <br>
  
    
