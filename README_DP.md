
# DP

## 소개글

DP 데이터셋은 주어진 문장을 의존 구문 분석(Dependency Parsing)한 데이터셋입니다. 

(*해당 데이터셋은 한국어 자연어 이해 평가 벤치마크인 [KLUE](https://klue-benchmark.com/) 데이터셋의 일부이나, 기존 벤치마크와는 다름을 알립니다.*)

## 특징

DP 데이터셋은 TTA 표준 의존구문분석 가이드라인(https://aiopen.etri.re.kr/data/003.%EC%9D%98%EC%A1%B4%EA%B5%AC%EB%AC%B8%EB%B6%84%EC%84%9D_%EA%B0%80%EC%9D%B4%EB%93%9C%EB%9D%BC%EC%9D%B8.pdf) 을 기반으로 주석되었습니다. 본 데이터에는 형태소 분석 정보도 포함되어 있으며, 형태소 분석은 TTA 표준 형태소 태깅 말뭉치 작성용 가이드라인(https://aiopen.etri.re.kr/data/001.%ED%98%95%ED%83%9C%EC%86%8C%EB%B6%84%EC%84%9D_%EA%B0%80%EC%9D%B4%EB%93%9C%EB%9D%BC%EC%9D%B8.pdf) 을 토대로 KLUE 데이터셋 구축 기준에 맞춰 진행하였습니다. 
 
상세한 정보는 [KLUE 논문](https://arxiv.org/abs/2105.09680)의 Dependency Parsing 섹션에서 확인하실 수 있습니다.

## 포맷

DP 데이터셋은 CoNLL 형식과 유사한 형식으로 작성되었습니다. 
데이터셋은 다음과 같은 구조를 가지고 있습니다. ## 기호 뒤에 원본 문장이 제시되며, 문장을 어절 단위로 분석하고 있습니다. 따라서 전체 행(Row)의 수와 문장의 어절 수가 일치합니다. 각 행은 총 여섯 개의 열(column)으로 이루어져 있으며, 각 열은 인덱스(ID, word index ), 어형(FORM, word form), 대표형(LEMMA, lemma of word form ), 형태 분석 태그(POS, part-of-speech tag), 핵((HEAD, head of the current word), 의존 관계 분석 태그(DEPREL, dependency relation)로 구성되어 있습니다.

    ## DP-0-000000  훌륭한 숙소 쾌적한 공간 호스트와의 의사소통의 어려움, 체크인의 복잡함만 빼면 완벽.       
    1 훌륭한 훌륭하 ㄴ VA+ETM  2 VP_MOD
    2 숙소  숙소  NNG 4 NP_CNJ
    3 쾌적한 쾌적하 ㄴ VA+ETM  4 VP_MOD
    4 공간  공간  NNG 11  NP
    5 호스트와의 호스트 와 의 NNG+JKB+JKG 6 NP_MOD
    6 의사소통의 의사 소통 의 NNG+NNG+JKG 7 NP_MOD
    7 어려움,  어렵 음 ,  VA+ETN+SP 9 VP_CNJ
    8 체크인의  체크인 의 NNG+JKG 9 NP_MOD
    9 복잡함만  복잡하 ㅁ 만 VA+ETN+JX 10  VP_OBJ
    10  빼면  빼 면 VV+EC 11  VP
    11  완벽. 완벽 .  NNG+SF  0 NP

의존 관계 분석 태그에 대한 설명은 다음과 같습니다. 

| Label   | Type  | Description   |
|---  |---  |---  |
| NP    | 구문  | Noun Phrase, 체언 (명사, 대명사, 수사)   |
| VP    | 구문  | Verb Phrase, 용언 (동사, 형용사, 보조용언)   |
| AP    | 구문  | Adverb Phrase, 부사구  |
| VNP   | 구문  | Copula Phrase, 긍정 지정사구 (명사+이다)  |
| DP    | 구문  | Adnoun Phrase, 관형사구   |
| IP    | 구문  | Interjection Phrase, 감탄사구 (호칭 및 대답 등의 표현)   |
| X   | 구문  | Pseudo Phrase, 의사구 (조사 단독 어절 또는 기호 등)   |
| L   | 구문  | Left Parenthesis and Quotation Mark, 부호 (왼쪽 괄호 및 따옴표)   |
| R   | 구문  | Right Parenthesis and Quotation Mark, 부호 (오른쪽 괄호 및 따옴표)   |
| SBJ   | 기능  | Subject, 주어   |
| OBJ   | 기능  | Object, 목적어   |
| MOD   | 기능  | Noun Modifier, 관형어 (체언 수식어)   |
| AJT   | 기능  | Predicate Modifier, 부사어 (용언 수식어)  |
| CMP   | 기능  | Complement, 보어  |
| CNJ   | 기능  | Conjunction, 접속어 (~와)   |


## 구성 
 
다음은 데이터의 구성입니다.
```
# 전체 데이터
./dataset/
  # 학습에 사용할 데이터셋. train 제공.
  ./train/
    # 학습용 train set
    ./train.csv
```

학습 데이터로는 총 7,000개의 문장이 제공됩니다.
검증 데이터로는 총 2,000개의 문장이 제공됩니다.
 
## 사용
 
 ### 라이센스
 
 [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
 
 ### Contact
 
 작성자: 한지윤 jiyoonhan@upstage.ai
