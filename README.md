# 교육통계 프로젝트
### 요약
사교육비를 중심으로 다양한 시•도별 데이터의 상관관계를 파악하고자 대시보드를 만들었다. 대시보드에서 사용자가 보고 싶은 상관 관계를 x,y 축 데이터를 조정함으로써 쉽게 볼 수 있도록 했다. 또한 상관 분석 및 추세선 추가를 통해 유의한 상관 관계가 있는지, 양(+)의 상관관계인지 음(-)의 상관관계인지 알 수 있도록 하였다.

### 서론
대시보드(Dashboard)란 각종 정보를 한 눈에 볼 수 있도록 디자인된 페이지나 화면을 말하며 일종의 보고서이기도 하다. 여러 개의 그래프나 표, 수치 등을 하나의 페이지에 집약해 놓은 데다 상호작용이 가능하여 원하는 항목이나 시기 등을 보기 쉽기 때문에 상관관계나 흐름을 파악하기에 용이하다.  
사교육비를 비롯한 몇 가지 데이터의 상관관계를 알아보기 쉽게 다양한 상호작용과 분석 결과를 대시보드와 함께 제공하였다. 이를 통해 교육 통계 팀 프로젝트의 결과를 한 눈에 보여주고 결과 분석을 수월하게 하는 것을 목적으로 하였다.

### 방법
1. x축과 y축 변수를 (Indicator Name == ‘변수’) 형태로 지정할 수 있도록 Indicator Name 컬럼을 생성한다. 각종 진학률, 사교육비, 음주⬝흡연율 등을 Indicator Name 컬럼으로, 그 값을 value 컬럼으로 저장한다.(Indicator18_22.csv 데이터프레임)
2. 상관관계를 보여주는 산점도 그래프를 중심으로 대시보드를 생성했다. 그리고 산점도 그래프의 x축과 y축 값을 연도별로 볼 수 있는 꺾은선 그래프 2개를 보여주도록 만들었다.
3. scipy 라이브러리의 stats.spearmanr 함수를 이용해 산점도 그래프의 좌상단에 spearman 상관 분석 결과를 띄운다.(edu_stats2.py의 93-96번 줄)
4. plotly express의 trendline 함수를 이용해 c와 마찬가지로 산점도 그래프에 추세선을 추가한다.(edu_stats2.py의 90번 줄)
5. 일반 실행 파일과 flask를 통한 실행 파일을 생성하고, flask를 통해 로컬 호스팅한다.
    1. 프롬프트에서 실행 파일이 있는 경로로 이동한다.
    2. 다음의 명령어를 입력한다.
    3. ```powershell
       set FLASK_APP=edu_stats2.py
       flask run
       ```
6. 웹 브라우저에서 http://127.0.0.1:5000 로 접속한다.

| ![image](https://github.com/jjun2648/edustats/assets/50532905/3f14a733-0b26-4921-9d09-835830ed5bb3) |
|:--:|
| <b> [Figure1] Dashboard 생성 Workflow </b> |
| 전처리된 데이터프레임을 Indicator Name 컬럼을 추가하여 변경했다. 이후 대시보드를 만들고 분석을 위한 요소를 추가했다. |

### 결과
| ![image](https://github.com/jjun2648/edustats/assets/50532905/b83ece28-b88c-4fff-91b8-1e1168627599) |
|:--:|
| <b> [Figure2] Flask의 로컬 호스팅을 통해 실행한 Dashboard 화면 </b> |
| 대시보드의 기본 화면. 사교육비와 특목고 진학률을 기본으로 보여주고 지역은 서울이 지정되어 있다. 사교육비와 특목고 진학률은 상관관계가 없는 것을 볼 수 있다. |

### 버젼 및 라이브러리
Python(3.10.9)
dash Python package (version 2.9.3)  
Flask Python package (version 2.2.2)  
pandas Python package (version 1.5.3)  
plotly Python package (version 5.9.0)  
scipy Python package (version 1.10.0)  
