# Ubion_Project2

유비온디지털센터에서 진행한 최종 프로젝트
 
주제 : 텍스트마이닝을 활용한 기업부도예측 모형 연구                 

부도의 정의
---
상장폐지가 결정된 기업들 중 실적 부진과 관련된 이유로 상장폐지된 기업을 부도 기업으로 간주

기업 부도 여부 데이터 수집 기간 (2011 - 2021) KIND에서 수집
---

재무 비율 데이터 수집 기간 (2009 - 2019) TS2000에서 수집
---
직전연도의 재무비율 사용시 이미 악화된 재무비율을 사용함으로써 부도 예측의 오류 발생 가능성이 높기 때문에
2년전 재무비율 사용. 

텍스트 데이터 수집 기간
---
부도기업의 경우 상장폐지가 3개월 전에 이미 확정나므로 부도 예측의 오류 발생을 막기위해
상장폐지일 - 3개월에서 1년간의 데이터 수집 정상기업의 경우 회계결산일로부터 1년간의 데이터 수집

진행기간 : 2022.06.07 ~ 2022.07.08  
---
프로젝트 세부 내역
---
notion url : https://dbswo601.notion.site/f85f51d49a3d4dc7b02e538c75b63798

이 프로젝트는 코스닥에서 제조업 기업들을 대상하며 텍스트 데이터를 사용함으로써 모델에 적시성을 반영한다.
또한 부도 예측 과정에서 재무비율만을 사용할 때보다 뉴스 기사와 같은 텍스트 데이터를 활용할 때 예측력이 
향상되는지, 텍스트 데이터를 어떤 방식으로 가공할 때 더 높은 성능을 보이는지 확인해보는 연구이다.
분석 결과로는 재무비율만을 사용할 때보다 텍스트 데이터를 같이 사용할 때 높은 성능을 보임으로써
텍스트 데이터의 유의성을 확인할 수 있었다.  

DATA SET (1) : 재무비율 <br>
DATA SET (2) : 재무비율 + 부도기사비율(Word2Vec) <br>
DATA SET (3) : 재무비율 + 부정기사비율(SentiWordNet 감성분석)

기업부도예측에 사용할 최종 선정된 DATA SET과 모델의 조합
---
(DATA SET (2) 재무비율 + 부도기사비율) + SVM

자동화 파일 사용
---
자동화에 있는 파이썬 파일은 부도 예측 프로세스를 하나로 압축한 것이며 
해당 폴더의 최종.csv파일을 데이터베이스에 입력 후 py파일을 실행하고 원하는 기업을
입력하면 해당 기업이 데이터베이스에 존재할 경우 DB에서 재무비율을 가져오고
현재 시점 - 3개월을 기준으로 1년간의 뉴스를 수집해서 전처리 후 
부도 기사 비율로 만들어 기업의 1년내 부도를 예측한다.  

파이썬 3.8.0 버전에서 작동시킬 수 있다.

