# 2019147006 박호찬_Final Project
## **프레젠테이션은 Presentation.pdf 로 업로드 했습니다.**  
## 아래 Readme 파일은 pdf 파일에 대한 요약본입니다.

### 1차 모델은 Base Strategy에 대한 벡테스터 객체와 그에 필요한 내부, 외부 method를 구현한 .py 파일입니다.
### 2차 모델은 머신러닝을 활용합니다. 이후 성능 평가를 가시적으로 보이기 위해 .ipynb 파일로 작성했습니다.  

### Abstract: 'Advances in Financial Machine Learning'에 기반한 KOSDAQ 150 지수 데이터를 이용해 백테스팅 엔진 구현  

1. Minute Data(High Frequency Data) 이용
   원래는 KOSPI Tick Data를 이용하여 시간 단위로 나뉘어져 있는 가격 데이터를 거래 금액/거래량 기준으로 재구성 하는 과정이 있었는데(한 차트 바 데이터에 들어가는 정보량을 균등하게 맞춰주는 작업)  
   유료 데이터인 관계로(공개하지 않아도 된다고 하셨지만) 아무래도 데이터를 공개할 수 있는 KOSDAQ150 지수의 분 단위 데이터를 활용하게 되었습니다.
2. 1차 Base Model(Trading Strategy) 구축 : Price Momentum 강도를 판단할 지표와 이상치 구분을 위한 Parkinson Volatility 사용
3. 금융 데이터에 맞게 적당한 기법 사용 : Tripple Barrier(시계열적 상관성이 높은 금융 데이터를 다루는 일종의 기법) & Meta Labeling(시그널이 True Positive인지 False Positive인지에 대한 Binary Label)
4. 2차 Machine Learning Model 구축 : Random Forest 이용 > Base Model의 Signal의 True/False 여부 판단하는 모델

### Data
1. main data : KQ150 분 단위 데이터, 2016-2023년까지의 데이터(사이즈가 너무 커서 압축파일로 올려놓았습니다)  
2. entrance_exit : Base Strategy가 발생시키는 시그널  
3. tri_barrier : Main Data와 변동성을 기준으로 박스권 생성(일종의 Partition 생성 - 자세한 내용은 생략) 
4. m_labels : 시그널에 대한 True Positive, Negative Positive를 나타내는 Binary Label (Random Forest의 target이 되는 데이터)  


### Python
1. StocTestFinal : 1차 모델에 대한 벡테스터 객체 구현 > entrance_exit 파일 생성
2. tb_mlabel_rf : 2차 모델 구현을 위한 전처리(Tripple Barrier, Meta Labeling 진행) > 2차 모델인 Random Forest 구현 > 최종 ROC Curve를 통한 성능 평가

기타 내용은 PDF 파일 안에 정리해놓았습니다.


