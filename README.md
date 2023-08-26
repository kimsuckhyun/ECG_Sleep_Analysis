# ECG_Sleep_Analysis
### | [Data](https://drive.google.com/drive/folders/1G3M5D2xkpku9Uqs1zffJEhc8pAzf89it?usp=sharing)
[![Open Tiny-NeRF in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/bmild/nerf/blob/master/tiny_nerf.ipynb)<br>


## Setup

코드를 실행하기 위해서는 다음의 Python 3 라이브러리들이 필요합니다. 코드 실행 전에 반드시 설치해 주세요.

* Keras
* matplotlib
* numpy
* imageio
* configargparse
* scikit-learn
* pandas
* PyTorch
* scipy
* pickle
* random

`pip`를 사용하여 의존성을 설치할 수 있습니다:

```bash
pip install keras matplotlib numpy imageio configargparse scikit-learn pandas torch scipy
```

---
<img src='imgs/pipeline.jpg'/>

## DataSet
### Data acquisition method
- 본 연구의 참가자(25세-32세 사이 남성) 7명은 졸음에
영향을 미치는 화학물질의 섭취를 통제하는 데에 동의했다.
실험전에 참가자들에게 카페인이 함유된 음료와 알코올을 5
시간, 24시간 동안 마시지 않도록 요청하였다. 또한 배고픔
으로 인한 졸음 억제를 피하기 위해 모든 참가자들은 식사
후 40분–70분에 실험을 시작했다. 일상적인 조건에서 생리
적 신호를 측정하기 위해 기상 후 시간, 일주기 리듬 변화,
생리적 활동을 고려하지 않고 자원자를 모집했으며 대부분
의 참가자들은 실험 전 날 노동 또는 운동 같은 많은 체력
이 소모되는 신체 활동을 수행하지 않았다고 답했다. 모든
참가자는 연구에 참여하기 전, 연구계획 (서울대학교 IRB No. 
C-1509-074-704)에 동의했고, 졸음 검출 실험을 진행하기
이전에 참가자들은 시뮬레이터와 작업에 익숙해지도록 하기
위해 5분동안 운전해 본 뒤 실험에 참여했다.

##### 하나의 mat file(sync_data_seatdr_s2)은 6가지의 데이터프레임으로 구성되어 있다.
- 그 중 프로젝트에 사용된 데이터프레임은 각각 data_event 와 sync_data_bio
  - data_event : 랜덤하게 차량이 흔들린 이벤트시점, 그로부터 반응시간, 흔들린 면적
  - sync_data_bio : ECG신호, 즉 심전도 데이터를 비롯한 중심부 혈압계, 호흡 등등 다양한 데이터가 포함된 프레임
---  
## Data_Setup
<img src='imgs/pipeline.jpg'/>


#####  반응시간 (Reaction Time, RT)
- 이상치가 제거된 반응시간을 Reaction Time(RT)이라고
하면, RT 는 운전자가 운전 중 일 때 졸음과 깬 상태에 따라
다르게 나타난다.
- 그림과 같이 Response – Forced move = Reaction 
Time (RT)으로 정의할 수 있으며, 반응시간이 클수록 졸음
상태에 가깝고 반응시간이 적을수록 깬 상태에 가깝다. 따라
서 우리는 깨어 있을 때 = 0, 졸았을 때 = 1로 label을 설정
하여 연구를 진행한다[4].
RT를 변수로 설정하여 x축은 RT(s)로, y축은 RT에 2를
빼고 2를 더한 값에 5를 나눈 평균값인 5-averaged RT(s)로
설정한다. 그림 4과 같이 실험자가 RT와 RT의 평균값이 1.4
를 초과하면 졸음상태(drowsiness)로 판단하여 빨간색으로
표시되고, RT와 RT의 평균값이 1미만이면 깬 상태(Alertness)
로 판단하여 파란색을 표시된다.
 
  - --------------------------------------------------------------------------------------------------------------------------------------
## 진행 과정
 
1. 데이터 EDA
2. 데이터 전처리  
3. 데이터 모델링
4. 모델 평가

## 실행방법
