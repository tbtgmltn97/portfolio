<img src="https://capsule-render.vercel.app/api?type=rounded&color=auto&height=200&section=header&text=Alsong-Dlsong&fontSize=90" />

## 🎤 Alsong-Dlsong이란?

**`알송달송`** 은 **이원화된 노래방 곡 데이터를 한 데 모아 검색 및 저장**하고, <br>
**저장된 곡을 기반으로 어울리는 부를 곡 추천**을 받을 수 있는<br> 
**`노래방 곡정보 저장 & 추천 모바일 웹 서비스`** 입니다. <br>

<br>

<details>
<summary>🎤 Alsong-Dlsong 바로가기</summary>
<div markdown="1">

<br>
<a href="http://alsong-dlsong.com" target="_blank" rel="noopener noreferrer">👉🏻Click👈🏻</a>
<br>
</div>
</details>

<br>

## 🧑‍🤝‍🧑 제작 기간 & 참여 인원

  	-  제작 기간 : 2023.06.01 ~ 2023.08.11 (약 2개월)
	-  참여 인원 : 6명
<br>

## ⚙️ 사용 기술 스택

<br>

| ⚙️ 기술 스택 | 👇🏻 사용 목적 |
|--|--|
| **`django`** | 알송달송 웹 서비스 구현 |
| **`fastapi`** | 추천 모델 serving |
| **`word2vec`** | 곡 추천 model 학습 |
| **`Google Cloud Storage`** | Data Warehouse, 학습된 모델 파일 적재 |
| **`airflow`** | 노래방 곡정보/인기차트 ETL 과정 자동화 , 모델 재학습 자동화|
| **`celery`**, **`rabbitmq`**, **`redis`** | 트래픽 분산, 로그 적재 |
| **`postgreDB`**, **`mongoDB`** | 데이터베이스 활용 |
| **`nginx`**, **`gunicorn`** | Web서버와 WAS 분리 |
| **`GCP(Google Cloud Platform)`** | 배포를 위한 클라우드 서비스 활용 |
| **`docker`**, **`docker compose`** | 배포를 위한 작업 환경 도커라이징 |
| **`elastic search`**, **`logstash`**, **`kibana`** | 검색 기능 고도화, 데이터 시각화 |
| **`OpenAI`** | ChatGPT를 활용해 추천 결과 예외 후처리 |
| **`kakaoAPI`** | 소셜 로그인 구현 |
| **`NiFi`** | 데이터베이스 이원화 및 동기화 |

<br>

## ERD 설계
	
![DB ERD](https://velog.velcdn.com/images/doodjb/post/a53bf08d-8745-4c30-9b71-b349b33da6bc/image.png)

<br>

## 데이터 수집 파이프라인
<div align="center">
	<img src="https://postfiles.pstatic.net/MjAyMzA4MTdfMjMw/MDAxNjkyMjQ2MjE3NTUx.o0hyA4hhxEtAwHoAsroynVTU0mh8E9Lq9eQKwR2p6xYg.JQSgusSk2cQAA1ucnztiS6seDq3Q4tkcopbQGlKuyKAg.PNG.tbtgmltn97/image.png?type=w773"/>
 
</div>
<br>

## 📖 모델 학습 파이프라인
<div align="center">
	<img src="https://postfiles.pstatic.net/MjAyMzA4MTdfNjQg/MDAxNjkyMjQ2MjQyMjg0.Mdrh_MhV4EsgSbLAWXLFFGpr9QbKyHEBSv_GuW66e64g.JL_Wle3hVNgZt9ovP6zZ7q_yhZt3mYjVWoexveWljeQg.PNG.tbtgmltn97/image.png?type=w773"/>
 
</div>

## 핵심 기능
이 서비스의 핵심 기능은 **추천 서비스 기능**입니다. <br>
사용자가 즐겨부르는 노래 리스트를 기반으로 새로운 곡을 추천해주는 서비스입니다. <br>
또한, 다른 플랫폼과 차별화할 수 있는 기능으로는 추천 모델이 사용자들의 **로그 데이터**를 통해 <br>
하루에 한번씩 **재학습**되어 어제와 오늘 다른 추천곡을 받아볼 수 있다는 점입니다.<br>
아래는 **전체 아키텍처**에 대한 첨부파일입니다.

<details>
<summary><b>전체 아키텍처 펼치기</b></summary>
<div align="center" markdown="1">
	<img src="https://camo.githubusercontent.com/fcdbff0cd3611dd22e758cdedfd8ca9002ef84be84a5b1620fdda2b10d35838b/68747470733a2f2f706f737466696c65732e707374617469632e6e65742f4d6a41794d7a41344d5464664e5467672f4d4441784e6a6b794d6a51314e7a637a4f544d302e44714568332d7441414c5f567672704b6c6a6468413650626b6d576555746d5a544469486c7442574e6e59672e776d7846375149706447564c714566666c7a7537725377646465366579474b394333675f61554245794e30672e504e472e746274676d6c746e39372f696d6167652e706e673f747970653d77373733"/>
</div>
</details>

## 트러블 슈팅

### 1. Airflow 경로 이슈
- Airflow는 되도록이면 상대 경로가 아닌 절대 경로를 사용! <br>
#### 1-1. 상대경로로 명시한 코드 (에러 발생)
<img src="https://postfiles.pstatic.net/MjAyMzA3MjBfMjA4/MDAxNjg5ODM1MjE0MDgz.crL53KYPTa5xls9BndveVU73e7IjB8JcbSKIX2o2nYgg.Z5AcurZS7JTQ1IDub6gd2rbTmn_k6afrWf4u8ZUvZDkg.PNG.tbtgmltn97/image.png?type=w773"/>

#### 1-2. 절대경로로 명시한 코드 (에러 해결)
<img src="https://postfiles.pstatic.net/MjAyMzA3MjBfOCAg/MDAxNjg5ODM1MTg2MTg3.49txacmApMoHOnzY6-X0vKGSeMjLWMR8nPeO4tUCC7kg.KEuBjbfMK8mybviSZ1wFfvqFYbjFz6NJpRwHax6yFscg.PNG.tbtgmltn97/image.png?type=w773"/>

<br>

<details>
<summary>💣 자세한 Trouble shooting 기록</summary>
<div markdown="1">

<br>
<a href="https://blog.naver.com/tbtgmltn97/223161573632" target="_blank" rel="noopener noreferrer">👉🏻Click👈🏻</a>
<br>
</div>
</details>
<br>

### 2. Airflow 권한 이슈
- 호스트에 마운트 한 디렉터리의 권한을 올바르게 설정해주기!<br>
	- docker 컨테이너에서 파일시스템 볼륨을 마운트할 때, 해당 볼륨에 대한 권한을 호스트에서 가져오게 되는데, 이 권한은 **호스트에서 마운트 한 디렉터리의 소유자와 그룹에 따라 결정**된다.<br>
 	- 즉, 호스트에서 마운트 한 디렉터리가 docker 컨테이너에 마운트 되면, 컨테이너 내부에서 이 디렉터리에 포함된 파일에 대한 작업을 수행할 때 **호스트의 권한으로 작업하게 된다.**

<br>

<details>
<summary>💣 자세한 Trouble shooting 기록</summary>
<div markdown="1">

<br>
<a href="https://blog.naver.com/tbtgmltn97/223175583093" target="_blank" rel="noopener noreferrer">👉🏻Click👈🏻</a>
<br>
</div>
</details>
<br>

### 3. mongoDB connection issue
- pymongo를 통해 python에서 mongoDB에 접근할 때 권한 인증 제대로 명시해주기!

<br>

<details>
<summary>💣 자세한 Trouble shooting 기록</summary>
<div markdown="1">

<br>
<a href="https://blog.naver.com/tbtgmltn97/223179578228" target="_blank" rel="noopener noreferrer">👉🏻Click👈🏻</a>
<br>
</div>
</details>
<br>

### 4. GCP에 FTP 서버 연결 issue
- GCP에 등록한 공개키에 대한 개인키를 filezilla에 제대로 추가하기<br>
- 인스턴스의 20,21번 포트 열어주기<br>
- sftp를 통해 접근하기

<br>

<details>
<summary>💣 자세한 Trouble shooting 기록</summary>
<div markdown="1">

<br>
<a href="https://blog.naver.com/tbtgmltn97/223187187278" target="_blank" rel="noopener noreferrer">👉🏻Click👈🏻</a>
<br>
</div>
</details>
<br>

### 5. SSH를 통한 GCP 인스턴스 접속 issue (디스크 용량 부족)
- 인스턴스의 디스크 용량이 부족하면 SSH 서버가 종료될 수 있다.

<br>

<details>
<summary>💣 자세한 Trouble shooting 기록</summary>
<div markdown="1">

<br>
<a href="https://blog.naver.com/tbtgmltn97/223175565888" target="_blank" rel="noopener noreferrer">👉🏻Click👈🏻</a>
<br>
</div>
</details>

<br>

## 내가 맡은 큰 틀
<br>

### 1. 모델 생성
<br>

	모델을 생성할 때 딥러닝 또는 머신러닝에 많은 지식을 갖고 있지 않았기 때문에 많은 어려움을 겪었습니다.
 
 	또한 추천이라는 특정 주제가 성능을 나타내기 힘든 점이 있어 모델 간 성능 비교를 하지 못한 한계점이 있습니다.
    관련 논문을 찾아보니 "음악을 듣는(부르는) 순서에는 음악 간의 유사성에 대한 풍부한 정보가 담겨져 있고,
	현재 듣는(부르는) 노래는 사용자의 감정을 불러 일으켜 후속곡 선택에 영향을 미친다." 라는 문장을 확인하였고, 
 	저희 프로젝트에 굉장히 부합되는 생각이라고 판단하였습니다.
  
 	위의 내용으로 통해 저희가 Word2Vec을 통해 모델을 학습시킨 이유는 아래와 같습니다.
  
  	첫째, 사용자들의 평점이 없어도 구현이 가능하다.
   
   	둘째, 플레이리스트 단위로 학습을 하므로 플레이리스트에 담긴 곡들의 맥락이 반영된다.
    
    셋째, 플레이리스트의 노래간 문맥을 파악한 추천이 가능하다.
    
    넷째, 쉽고 빠른 구현이 가능하다.


### 2. Airflow를 통한 ETL 파이프라인 구축
<br>   	
	
 	Airflow를 통해 TJ, KY에서 데이터를 크롤링(수집)하여 Google Cloud Storage에 적재하고 
 	필요한 데이터를 전처리 후 PostgreSQL로 전송하는 일련의 과정을 자동화하였습니다.

  	위의 내용을 자동화하는 과정 중에서 DB에 적재할 때 PK, FK 때문에 생기는 중복에 대한 처리도 해주었습니다.

	또한 celery를 이용할 때 로그 데이터를 redis에 임시저장을 해주는 로직을 구현하여, 
 	redis에서 특정 날짜에 들어온 데이터만 mongoDB로 전송하는 과정도 자동화했습니다.
  
	mongoDB에 있는 데이터를 모델의 학습 데이터로 다시 사용하는 과정도 자동화시켜 하루마다 모델이 업데이트됩니다.

 	즉, 모든 일련의 과정이 자동화되어 지속적으로 서비스가 제공될 수 있게 설계하였습니다.


### 3. DB 서버 구축
  <br>
	
  	저희 데이터를 수집, 사용하기 위해 DATABASE가 필요하여 DB서버를 구축하였고,
   	DB서버와 다른 인스턴스끼리 통신을 할 수 있게 설정을 해주었습니다.
    
   	사용한 DATABASE는 다음과 같습니다.
    	
	실제 서비스를 위한 데이터, 사용자에 대한 데이터 적재 => PostgreSQL
	로그 데이터 임시 저장 => Redis
	로그 데이터를 모두 적재 => MongoDB

 	저희 서비스는 도커라이징을 통한 배포를 하였으나, DB 서버는 보수적인 관리를 위해 도커라이징을 하지 않았습니다.

### 4. DB 이원화
  <br>

  	사용자 데이터가 있는 DB를 더욱 보수적으로 관리할 방법을 모색하던 중, DB를 개발DB와 운영DB로 이원화하기로 하였습니다.

	DB 이원화를 하는 방법으로 DB 복제라는 방법도 있었지만 특정 시점에만 DB가 복제된다는 한계가 있다고 판단하여,
	Apache NiFi를 사용해 1초 간격으로 DB가 동기화되는 방법으로 DB를 이원화해주었습니다.

	하지만 위와 같은 방법으로는 과금이 된다는 단점이 있어서 배치 간격을 6시간 간격으로 늘려주었습니다.

