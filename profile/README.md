# 2023 한이음 ICT 멘토링 프로젝트 - 잡았다 요놈 팀

## 프로젝트 주제 및 내용
- 주제: <b>나의 웹 컨텐츠를 지키기 위한 크롤링 탐지 봇</b>
- 내용
  > - ChatGPT, NovelAI 등 인공지능의 발달에 따라 웹 컨텐츠를 학습 데이터로 쓰기 위해 무단 크롤링이 증가하여 웹 컨텐츠의 저작권 침해와 더불어 웹 서버의 트래픽 부담이 증가하였다.
  > - 본 프로젝트는 클라우드 환경에서 배포되는 웹 서버의 악성 크롤링을 막고자 ALB 로그의 수집, 로그 데이터 적재(OpenSearch), 크롤링 트래픽 탐지, WAF를 통한 접근 차단 등을 자동화하여 웹 컨텐츠를 보호하고, Kibana를 통해 차단된 트래픽을 모니터링 할 수 있도록 한다.
  > - 또한, Slack봇을 연동하여 악성 크롤링 탐지 시 알림을 받을 수 있도록 하며 원격 제어 기능을 추가한다.

## 프로젝트 결과

### 시연영상

- https://youtu.be/G1z5hg_Jb-o?si=_dqBxe-udsReKI0O

### 아키텍처

![architecture drawio](https://github.com/DEU-hanium/.github/assets/57895643/23cecc4e-81fc-4d4c-ae34-f3ed8c46b6bc)




## 기능별 구현 내용

- [ALB 트래픽 로그 OpenSearch에 적재하기](https://github.com/DEU-hanium/.github/blob/main/profile/opensearch_load/opensearch_load.md)
- [OpenSearch에 적재된 로그 데이터를 통해 악성 크롤링 탐지하기](https://github.com/DEU-hanium/.github/blob/main/profile/detect_crawling/detect_crawling.md)
- [FastAPI 서버로 WAF 접근 차단하기&Slack api 구현](https://github.com/DEU-hanium/.github/blob/main/profile/FastAPI_SlackAPI/FastAPI_SlackAPI.md)
- [Opensearch Kibana 시각화 하기](https://github.com/DEU-hanium/.github/tree/main/profile/visualization/visualization.md)

## 프로젝트 참여자

- 전성신(멘토)
- 임종훈(팀장)
- 김준기
- 이상진
- 남정욱
- 최서윤
