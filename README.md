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
