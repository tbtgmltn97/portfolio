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
<a href="http://alsong-dlsong.com" target="_blank">👉🏻Click👈🏻</a>
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

</details>


