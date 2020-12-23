# sentiment_analysis-202012-
first trial for sentiment analysis by shcho11
한글 / 영어 감정분석기 시험
1. text preprocessing
  1) word tokenize 단어 분리 (문장 분리)
  2) 형태소 분석 (input: (1)에서 tokenized words(품사태깅))(한국어 / 영어 라이브러리 다름)
  3) 개체 인식 (input: (2)에서 형태소 태깅 리스트)
  4) Edit Distance #진행X
  5) Stemming (어간추출) #Porter Stemming Algorithm
  6) Lemmatization (단어 원형, 즉 표제어 찾기)
  7) Stopword (불용어) 제거

2. N-gram language modeling (Unigram LM , Bigram LM, Trigram LM) (N-gram 기반 언어모델, WSD 실습)
  - import nltk
  - from nltk.util import ngrams

3. Scikit-learn (Scikit learn 을 이용한 전통적인 기계학습 기반 자연언어처리)
  1) Machine learning (머신러닝)
  2) Text Classification (텍스트 분류)
  - Load dataset (데이터셋 로딩)
    - from sklearn.datasets import fetch_20news
  - Extract features from text (텍스트 특징 추출)
    - from sklearn.feature_extraction.text import CountVectorizer
  - Trainig a classifier (분류사 학습)
    - from sklearn.naive_bayes import MultinomialNB
  - Evaluating on testset (테스트셋 평가)

4. Keras
  1) 입력 텐서의 타겟텐서로 이루어진 훈련 데이터를 정의
  2) 입력과 타겟을 mapping하는 층(layer)로 이루어진 모델 (혹은 네트워크)를 정의
  3) 손실함수(loss function), 옵티마이저(Optimizer), 모니터링을 하기 위한 측정 지표를 선택, 학습과정을 설정.
  4) 훈련 데이터에 대해 모델의 fit() 메서드를 반복적으로 호출, 훈련을 시작.
  
  * 리스트를 텐서로 바꿔줘야 하는데, 2가지 방법 있음
  - (1) 같은 길이가 되도록 List에 padding을 추가, (samples,sequence_length)크기의 정수 텐서로 변환. 그 다음 이 정수텐서를 embedding layer로 사용.
  - (2) List를 One-hot Encoding하여 0과 1의 벡터로 변환
  * 층을 깊게 만드는 장점 살리기 위해 비선형성 또는 활성화함수 추가해야 함. 주로 relu많이 사용.
  
5. CNN 이용한 감정분석
  1) 데이터 다운로드
  2) 패키지 선언 및 Glove 다운로드
  3) 학습 데이터와 평가 데이터
  4) Keras 통한 전처리 과정
    (1) Text를 tokenize하여 id값으로 변경. (tokenizer.texts_to_sequences)
    (2) id로 변경해준 문장들을 모두 문장 최대길이로 padding 처리. (pad_sequences)
  5) 모델 설정
    (1) Random으로 초기화된 embedding이 아닌, 사전훈련된(pre-trained) GLoVE embedding으로 학습
    (2) therefore, 학습 코퍼스에 있는 단어들 중 GLoVE embedding에 있는 단어들을 GLoVE embedding으로 초기화 해준다.
    (3) 본 실험에서는 GLoVE 임베딩 크기가 50인 것과 100인 것을 통해 실험 진행
  6) Accuracy와 Loss 시각화
  7) CNN 모델 선언
    (1) Convolution 필터를 앞서 배운 것 처럼 여러개 사용
    (2) 본 모델에서는 Window Size가 2,3,4,5인 필터 각 100씩 사용하여 모델 학습
    * (다양한 크기 필터 사용하면 성능이 올라갈까?) : 정답은 "올라간다" Convolution 필터가 보는 단어의 갯수가 다양하게 되기 때문에, 문장의 local 정보와 global 정보 모두 학습할 수 있음.
    
