# 2023 한이음 ICT 멘토링 프로젝트 - 잡았다 요놈 팀

## 프로젝트 주제 및 내용
- 주제: <b>나의 웹 컨텐츠를 지키기 위한 크롤링 탐지 봇</b>
- 내용
  > - ChatGPT, NovelAI 등 인공지능의 발달에 따라 웹 컨텐츠를 학습 데이터로 쓰기 위해 무단 크롤링이 증가하여 웹 컨텐츠의 저작권 침해와 더불어 웹 서버의 트래픽 부담이 증가하였다.
  > - 본 프로젝트는 클라우드 환경에서 배포되는 웹 서버의 악성 크롤링을 막고자 ALB 로그의 수집, 로그 데이터 적재(OpenSearch), 크롤링 트래픽 탐지, WAF를 통한 접근 차단 등을 자동화하여 웹 컨텐츠를 보호하고, Kibana를 통해 차단된 트래픽을 모니터링 할 수 있도록 한다.
  > - 또한, Slack봇을 연동하여 악성 크롤링 탐지 시 알림을 받을 수 있도록 하며 원격 제어 기능을 추가한다.

## 프로젝트 결과

### 아키텍처

![image](https://drive.google.com/uc?id=18NggB4dBvqAYDxQD4-lvyhjf9AJYn2eX)

### 기능

1. 차단 IP Slack 알림
   
    ![image](https://drive.google.com/uc?id=1Cxl5zqTSKUcPvZ4ZrtvvlPRmUBUatBV4)

2. 차단 IP 목록 출력

    ![image](https://drive.google.com/uc?id=1GQjPcCTSN3rfIzUSJzE5HRwg95izHXta)

    ![image](https://drive.google.com/uc?id=17IGGyHLRWzmcMRPtrIA7ZHqxFvKkI7wJ)

3. 차단 IP 해제
   
    ![image](https://drive.google.com/uc?id=1qUZW5AC8e5yl4fY6fecEsrWXjbJC-R8Q)

4. 허용된 IP 목록 출력

    ![image](https://drive.google.com/uc?id=1ajnL7PRhHPbVa_blNb2Dusvx5CjyQbdP)

    ![image](https://drive.google.com/uc?id=1hU6_lZ5VVtFF5cIv6uAgRXiYWJHZnHUj)

5. 차단된 트래픽 시각화

    ![image](https://drive.google.com/uc?id=1umCfIjr784imNll2-dTayKWzsS6PColW)

6. 차단된 IP 위치 정보 시각화

    ![image](https://drive.google.com/uc?id=13DQ-U9A9joA6_-7TlDvDYGMImvhURxG0)

## 기능별 구현 내용

- [ALB 트래픽 로그 OpenSearch에 적재하기](https://github.com/DEU-hanium/ELBLogs-to-OpenSearch)
- OpenSearch에 적재된 로그 데이터를 통해 악성 크롤링 탐지하기(업로드 예정)
- FastAPI 서버로 WAF 접근 차단하기&Slack api 구현(업로드 예정)
- Opensearch Kibana 시각화 하기(업로드 예정)


## 프로젝트 참여자

- 전성신(멘토)
- 임종훈(팀장)
- 김준기
- 이상진
- 남정욱
- 최서윤