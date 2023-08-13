# 1. WAF

## 1.1 Create web ACL
> - Region: Asia Pacific (Seoul)
> - Name: crawling-WAF
> - Add AWS resources - Application Load Balancer에 만들어둔 ALB 선택

![image](https://drive.google.com/uc?id=1piiN_JVu8pSmv3RYueiujbjaFwSG_b5Z) 

## 1.2 Create IP set
> - IP set name: ban_list
> - Region: Asia Pacific (Seoul)

![image](https://drive.google.com/uc?id=1d2MNsVO3XuV63MlcMeYJIYnEWyLZJ-Ye)

## 1.3 Add rules
> - 만들었던 Web ACLs(crawling-WAF) - Rules 클릭
> - 우측 중앙의 Add rules - Add my own rules and rule groups
> - Rule type - IP set
> - Rule Name: ban_rule
> - IP set: ban_list

# 2. Fast API

## 2.1 Fast API 인스턴스 추가
![image](https://drive.google.com/uc?id=1Uo_fDAsiqlQsheAIkAOX4r0HZmrDcmbt) 
> - t3.medium
> - 키 페어 생성
> - 보안그룹 추가 - ssh, http, https, 8000 포트

![image](https://drive.google.com/uc?id=1Lw_mRYkRRiRAfU9bC1FS41Cq0vXwlpeX)

## 2.2 ec2용 IAM 생성
![image](https://drive.google.com/uc?id=1IdJALecEeTCP0vmgfd2ANhhh_t_j4USu)
> - admin - AdministratorAccess
> - 인스턴스 - 보안 - IAM 역할 수정

## 2.3 탄력적 IP 주소 할당
> 할당한 뒤 주소 연결(인스턴스 - FastAPI)

# 3. FastAPI-key.pem 키페어 설정

## 3.1 터미널 설정
```
chmod 600 test-instance.pem
```

## 3.2 config
```
Host fastAPI
  HostName IPv4주소
  User ec2-user
  port 22
  IdentityFile ~/.ssh/fastAPI-key.pem
```

## 3.3 새로운 vscode 터미널
```
sudo yum install git
git clone https://github.com/DEU-hanium/server.git
```

## 3.4 서버 터미널
```
curl -O https://bootstrap.pypa.io/get-pip.py
python3 get-pip.py --user
cd ..
pip install fastapi
pip install "uvicorn[standard]"
cd server
pip install boto3₩
pip install pymysql
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

## 3.5 .env 파일 만들기
```
curl -O https://bootstrap.pypa.io/get-pip.py
python3 get-pip.py --user
cd ..
pip install fastapi
pip install "uvicorn[standard]"
cd server
pip install boto3₩
pip install pymysql
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

# 4. slack

## 4.1 새로운 워크스테이션 만들기
[api.slack](https://api.slack.com/)
> create my first apps

## 4.2 slack 설정
> - incoming webhooks - on
> - oauth & permissions - workspace 복사해서 .env slack_token에 넣기
> - lambdaRouter.py 채널명 변경

![](https://drive.google.com/uc?id=1WKKZCGduS7txlXy4xZxkguyxS4O06WcR)

# 5. insert-data 생성

## 5.1 insert-data 함수 생성
> - python 3.10
> - 기존 역할 사용(lambda-admin)
> - 새로운 파일 만들어서 터미널에 아래의 코드 차례대로 작성
```
pip3 install --target ./package requests==2.29.0 requests_aws4auth
cd package
zip -r ../lambda.zip
cd ..
zip -g lambda.zip lambda_function.py
```
> zip에서 업로드

## 5.2 새로운 테스트 파일 만들기
> - sample.json
> - opensearch dev tools에서 json 긁어오기(아래는 테스트로 사용했던 json)
```json
[
  {
    "type": "http",
    "timestamp": "2023-07-15T10:56:52.880949Z",
    "elb": "app/crawling-ALB/ad89ac6140faaed1",
    "client_ip": "2.2.2.2",
    "clent_port": "58534",
    "target_ip": "172.31.14.236",
    "target_port": "80",
    "request_processing_time": "0.010",
    "target_processing_time": "0.001",
    "response_processing_time": "0.000",
    "elb_status_code": "404",
    "target_status_code": "404",
    "received_bytes": "211",
    "sent_bytes": "3828",
    "request_method": "GET",
    "url": "http://3.34.57.160:80/.env.prod",
    "http_version": "HTTP/1.1",
    "user_agent": "-",
    "ssl_cipher": "-",
    "ssl_protocol": "-",
    "target_group_arn": "arn:aws:elasticloadbalancing:ap-northeast-2:660477487349:targetgroup/crawling-TG/3b4f13f90cc98476",
    "trace_id": "Root=1-64b27b74-48a1136e06aa0d0646ec99ba",
    "domain_name": "-",
    "chosen_cert_arn": "-",
    "matched_rule_priority": "0",
    "request_creation_time": "2023-07-15T10:56:52.870000Z",
    "actions_executed": "waf,forward",
    "redirect_url": "-",
    "error_reason": "-",
    "target_port_list": "172.31.14.236:80",
    "target_status_code_list": "404",
    "classification": "-",
    "classification_reason": "-"
  },
  {
    "type": "http",
    "timestamp": "2023-07-15T10:56:52.880949Z",
    "elb": "app/crawling-ALB/ad89ac6140faaed1",
    "client_ip": "2.2.2.2",
    "clent_port": "58534",
    "target_ip": "172.31.14.236",
    "target_port": "80",
    "request_processing_time": "0.010",
    "target_processing_time": "0.001",
    "response_processing_time": "0.000",
    "elb_status_code": "404",
    "target_status_code": "404",
    "received_bytes": "211",
    "sent_bytes": "3828",
    "request_method": "GET",
    "url": "http://3.34.57.160:80/.env.prod",
    "http_version": "HTTP/1.1",
    "user_agent": "-",
    "ssl_cipher": "-",
    "ssl_protocol": "-",
    "target_group_arn": "arn:aws:elasticloadbalancing:ap-northeast-2:660477487349:targetgroup/crawling-TG/3b4f13f90cc98476",
    "trace_id": "Root=1-64b27b74-48a1136e06aa0d0646ec99ba",
    "domain_name": "-",
    "chosen_cert_arn": "-",
    "matched_rule_priority": "0",
    "request_creation_time": "2023-07-15T10:56:52.870000Z",
    "actions_executed": "waf,forward",
    "redirect_url": "-",
    "error_reason": "-",
    "target_port_list": "172.31.14.236:80",
    "target_status_code_list": "404",
    "classification": "-",
    "classification_reason": "-"
  }
]
```

## 5.3 환경변수 설정
> - HOST 추가
> - opensearchToLambda에 opensearch

## 5.4 lambda_function 코드 변경
> 13행 코드 변경
```python
def lambda_handler(event, context):
    index = 'logs'
    datatype = '_doc'
    url = host + '/' + index + '/' + datatype
    
    headers = { "Content-Type": "application/json" }
    
    with open('sample.json') as f:
        datas = json.load(f)
    
    for data in datas:
        r = requests.post(url, auth=awsauth, json=data, headers=headers)
        print(r.text)
```

# 6. opensearch to lambda test

## 6.1 모듈 수정
```
pip3 install --target ./package requests==2.29.0 requests_aws4auth pymysql
cd package
zip -r ../lambda.zip
cd ..
zip -g lambda.zip lambda_function.py
```
> - zip에서 업로드
> - 25행 gt: now-120m으로 수정해서 test

# 7. Database

## 7.1 내용
```
create table ban_list(
	ip varchar(20) primary key,
	memo varchar(10),
	created_at datetime default now()
);

create table require_list (
	ip varchar(20) primary key,
	memo varchar(10),
	created_at datetime default now()
);
```

## 7.2 환경변수
> opensearch-to-lambda 환경변수에서 DB: http://fastapi-ec2-ip:8000으로 변경

# 8. slack 설정 추가
![](https://drive.google.com/uc?id=119jLSVgM6rbTxKtkji37rc5gNSwP53tw)
> 위와 같이 해당 ip가 차단된 것을 확인할 수 있음

## 8.1 권한 설정
> - OAuth - scopes - add an OAuth Scope - chat:write 권한 주기
> - User Token Scopes - admin, chat write 권한 부여

![](https://drive.google.com/uc?id=1YFHZVA6of3ng_Y9tVDnSis7aFKM-YUaM)

## 8.2 .env 파일 변경
> .env slack_token에 user OAuth Token 넣어주기

## 8.3 create New Command
> - slash commands - create New Command
> - 아래의 사진처럼 채워주기

![](https://drive.google.com/uc?id=1fMoRU-_o0FaPmTKzVDXS6utlX6u7kUgY)
![](https://drive.google.com/uc?id=1klop2R3cgRRgORuf6qhBXIpUOTrukHhw)
