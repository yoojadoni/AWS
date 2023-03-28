### - 서버 환경
  - AWS(EC2), Linux

버전확인 명령어 : grep . /etc/*-release

#### 1. nginx가 있는지 확인
```
yum info nginx
```
nginx에 대한 경로가 없기 때문에 설정필요.

#### 2. nginx 레포 추가 및 확인
```
sudo vi /etc/yum.repos.d/nginx.repo
```
```
[nginx]
name = nginx repo
baseurl = http://nginx.org/packages/centos/7/$basearch/
gpgcheck = 0
enable = 1
```
vi편집기를 사용하여 위의 내용 입력.

아래의 명령어로 레포지토리가 추가된 것 확인한다.
```
yum info nginx
```

#### 3.nginx 설치
```
sudo yum install nginx
```
nginx의 버전 확인 방법
```
nginx -v
```

#### 4.nginx 시작 및 종료
시작
```
sudo systemctl start nginx
```
종료
```
sudo systemctl stop nginx
```

#### 5. 접속하여 정상 실행 확인하기
nginx를 시작해둔 상태로, IP로 접속하여 정상확인.


만약 연결할 수 없음 이나온다면 인바운드 규칙(방화벽) 확인 필요.
