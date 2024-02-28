# 프로젝트 소개 : 음성 기반 보이스피싱 감지 모델

이 프로젝트는 음성 파일에서 텍스트를 추출하고, 특정 키워드를 기반으로 보이스피싱 여부를 감지하는 간단한 모델을 구축한 것입니다.

## 개발기간

- 22.03 ~ 22.06

## 멤버구성

- 조일영(팀장) - 음성파일 및 데이터 수집, 분석
- 임승민(팀원) - 음성 파일 전처리, 텍스트 토큰화, 예측 모델 코드 작성
- 박시모(팀원) - 데이터 전처리

## 개발환경
- google colab
- python

## 기능

- 음성 파일에서 텍스트 추출
- 텍스트에 특정 키워드가 포함되었는지 여부를 확인하여 보이스피싱 여부 판별
- BERT 기반의 한국어 감정 분류 모델을 사용하여 텍스트 분류

## 프로세스

1. **음성 파일 전처리**
    - Google Speech Recognition을 사용하여 음성 파일에서 텍스트 추출
    - 추출된 텍스트를 CSV 파일에 저장

2. **데이터 전처리**
    - CSV 파일에서 텍스트와 레이블을 읽어옴
    - 특정 키워드를 포함하는지 여부에 따라 레이블을 할당

3. **텍스트 토큰화 및 모델 예측**
    - Hugging Face의 Transformers 라이브러리를 사용하여 BERT 기반 토크나이저와 모델을 로드
    - 텍스트를 전처리하고 모델에 입력하여 보이스피싱 여부 예측

    예시: Hugging Face의 Transformers 라이브러리를 사용하여 BERT 기반 토크나이저와 모델 로드
    ```
    tokenizer = AutoTokenizer.from_pretrained('kykim/bert-kor-base')
    model = AutoModelForSequenceClassification.from_pretrained('kykim/bert-kor-base')


5. **결과 출력**
    - 각 텍스트에 대한 실제 레이블, 모델 예측값, 스팸으로 분류될 확률을 출력

## 사용된 기술 스택

- [SpeechRecognition](https://pypi.org/project/SpeechRecognition/): 음성 파일에서 텍스트 추출
- [pandas](https://pandas.pydata.org/): 데이터 조작 및 CSV 파일 처리
- [transformers](https://huggingface.co/transformers/): BERT 모델 및 토크나이저 사용
- [torch](https://pytorch.org/): PyTorch를 사용한 딥러닝 모델 학습 및 예측

