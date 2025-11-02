# 1. 필요한 컬럼만 남기기
내가 사용할 데이터야.
난 여기서 아래의 컬럼만 필요해
먼저 컬럼을 분리하는 파이썬 코드를 줘.
id / title/ budget / popularity / genres / production_companies /production_countries /cast /director /writers / year/ month

난 캐글 노트북 환경이라서 
input data 경로는 /kaggle/input/viewer/TMDB_cleaned_data.csv
output 경로는 /kaggle/working/
이야 

# 2. 여러 장르를 행으로 나눠 저장/ 결측치 제거
앞으로 계속   사용할 데이터를 만들거야. 
먼저 방금 새로 만든 csv를 사용해서 
결측치를 발견하면  제거해줘. 

그리고 genres, production_countries, director, writer 컬럼을 보면 단어가 콤마로 연결되어 있는데 이를 각각 분리해서 컬럼으로 만들어줘.

이 과정을 거친 데이터를 csv로 저장하면 돼.

### 2- 답변
```
새로 만든 `selected_tmdb_data.csv` 파일을 사용해서 데이터 전처리를 진행하는 파이썬 코드를 작성해 드릴게요.

요청하신 작업은 다음과 같이 처리됩니다.

1.  **결측치 제거:** 분석의 일관성을 위해 데이터프레임 내의 모든 결측값(NaN)이 포함된 행을 모두 제거합니다.
2.  **데이터 분리 (Explode):** `genres`, `production_countries`, `director`, `writers` 컬럼은 하나의 행에 여러 값이 쉼표로 연결되어 있으므로, 각 쉼표로 구분된 요소를 개별 행으로 분리합니다 (`explode` 기능 사용). 이 방식은 영화 하나당 여러 장르/감독/작가/국가를 매핑하여 분석하는 데 유용합니다.

이 모든 과정을 담은 `data_preprocessing.py` 파일을 생성하고, 최종 결과는 `/kaggle/working/final_processed_tmdb_data.csv`에 저장됩니다.


http://googleusercontent.com/immersive_entry_chip/0

### 코드 설명 및 다음 단계

이 코드를 실행하면 다음과 같은 결과가 나옵니다.

* **결측치 제거:** 원본 데이터의 불완전한 행이 제거되어 분석의 신뢰도가 높아집니다.
* **데이터 확장:** Explode 작업 덕분에, 예를 들어 원본 데이터의 영화 하나가 'Action, Drama' 두 장르를 가지고 있었다면, 최종 데이터에서는 이 영화가 한 번은 'Action' 행으로, 다른 한 번은 'Drama' 행으로 총 두 번 나타나게 됩니다. 이는 각 장르, 국가, 감독, 작가를 기준으로 통계를 내거나 분석하는 데 매우 유리합니다.

이제 데이터를 분석하기 위한 준비가 거의 완료되었습니다. 이 데이터를 사용해 어떤 분석을 진행하고 싶으신가요? 예를 들어,

1.  **인기 분석:** 가장 인기 있는 (popularity 기준) 장르, 감독, 제작 국가는 무엇인지 찾아보기
2.  **수익성 분석:** `budget`과 `revenue`를 사용하여 영화의 수익성 지표를 계산하고 시각화하기
3.  **시계열 분석:** `year`와 `month`를 기준으로 시간이 지남에 따른 영화 트렌드 변화를 분석하기

다음 단계로 필요한 분석을 말씀해 주세요! 

[Image of a data analysis chart]

```

# 3. 장르별 인기 동향 시각화
내가 하려고 하는건 영화데이터의 '장르(genres)' 인기 동향에 대해 살펴보는거야. 

먼저 컬럼에 대해 설명해줄게
id:영화를 구분하는 번호 / title : 영화 제목/ budget : 영화를 제작하는데 든 비용 / popularity : 인기도 / genres : 해당 영화 장르 / production_companies : 제작사 /production_countries : 제작국가 /cast : 출연진 /director : 감독 /writers : 작가 / year : 개봉 연도/ month : 개봉 달

내가 하고 싶은 작업은
장르별 인기 동향을 확인할 수 있는 시각화 코드를 작성하는 것이야. 시간의 흐름에 따라 장르별 추세를 확인할 라인 차트를 그려줘. 그리고 시기별 장르 인기도를 비교하기 위해 누적 막대 그래프를 그려줘. 
