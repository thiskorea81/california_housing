# 🏡 캘리포니아 주택 가격 예측 프로젝트

이 프로젝트는 1990년 캘리포니아 인구조사 데이터를 기반으로 주택 가격을 예측하는 머신러닝 모델을 실습합니다.

## 📂 데이터셋

  - `california_housing_train.csv`: 모델 학습을 위한 훈련 데이터
  - `california_housing_test.csv`: 모델 성능 평가를 위한 테스트 데이터
  - **데이터 출처**: 1990년 캘리포니아 인구조사 데이터

## 📊 속성 정보 (Attribute Information)

| 속성명 (영문) | 속성명 (한글) | 설명 |
| :--- | :--- | :--- |
| `longitude` | **경도** | 지역의 경도 (서쪽으로 갈수록 음수) |
| `latitude` | **위도** | 지역의 위도 (북쪽으로 갈수록 양수) |
| `housing_median_age` | **주택\_중간\_연령** | 해당 지역 주택들의 중간 나이. 낮을수록 신축 건물이 많음. |
| `total_rooms` | **총\_방\_수** | 해당 지역의 총 방 개수 |
| `total_bedrooms` | **총\_침실\_수** | 해당 지역의 총 침실 개수 |
| `population` | **인구** | 해당 지역의 총인구 수 |
| `households` | **가구\_수** | 해당 지역의 총 가구 수 |
| `median_income` | **중간\_소득** | 해당 지역 가구의 중간 소득 (단위: $10,000) |
| `median_house_value` | **중간\_주택\_가격**| 해당 지역 주택의 중간 가격 (단위: $). **(예측 대상)** |

## 🚀 구글 코랩(Google Colab)에서 실행하기

구글 코랩 환경에서 아래 코드를 순서대로 실행하여 데이터를 간편하게 불러올 수 있습니다.

### 1\. GitHub 저장소 복제

`!git clone` 명령어를 사용하여 GitHub에 있는 데이터 파일들을 코랩 환경으로 가져옵니다.

```python
!git clone https://github.com/thiskorea81/california_housing.git
```

### 2\. Pandas로 데이터 불러오기

저장소 복제가 완료되면, `pandas` 라이브러리를 사용하여 두 개의 CSV 파일을 각각 DataFrame으로 불러옵니다.

```python
import pandas as pd

# 1. 복제된 폴더 안의 파일 경로 지정
train_file_path = '/content/california_housing/california_housing_train.csv'
test_file_path = '/content/california_housing/california_housing_test.csv'

# 2. 각 데이터 파일 불러오기
train_df = pd.read_csv(train_file_path, encoding = 'cp949')
test_df = pd.read_csv(test_file_path, encoding = 'cp949')

# 3. 데이터 탐색(EDA)을 위해 두 데이터프레임 합치기
df = pd.concat([train_df, test_df])

# 합쳐진 전체 데이터의 정보를 확인합니다.
print("--- 전체 데이터 정보 ---")
df.info()

# 🚨 중요: 합쳐진 데이터(df)는 데이터의 전반적인 특징을 살펴보는
# 탐색용으로만 사용해야 합니다. 모델 훈련은 train_df로,
# 모델 평가는 test_df로 진행해야 합니다.

# 훈련 데이터의 첫 5행을 다시 확인합니다.
print("\n--- 훈련 데이터 (Train Data) ---")
print(train_df.head())
```
