### AWS EC2에 Jenkins 설치.

- jenkins 기본 명령어
```
//시작
$sudo service jenkins start

//종료
$sudo service jenkins stop

//재시작
$sudo service jenkins restart

//젠킨스 상태보기
$sudo service jenkins status
```

#### 1. jenkins 설치 전 패키지 update 부터 진행
```
sudo yum update -y
```

#### 2. jenkins 설치 
- jenkins 공식 설치 가이드 문서 : https://pkg.jenkins.io/redhat-stable/
```
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
sudo yum install -y jenkins
```
- jenkins의 기본 포트는 8080이므로 변경 필요.
  - jenkins 종료
  ```
  sudo service jenkins stop
  ```
  - jenkins 포트변경 및 변경할 포트의 방화벽 오픈
  ```
  sudo vi /usr/lib/systemd/system/jenkins.service
  ```
  - jenkins 실행
  ```
  sudo service jenkins start 
  ```
- 설치 후 jenkins 서비스의 상태확인 
```
sudo systemctl status jenkins.service
```

- 설치 완료 후 기본 password 확인
```
sudo vi /var/lib/jenkins/secrets/initialAdminPassword
```


