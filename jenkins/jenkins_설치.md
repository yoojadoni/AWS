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
<img src="https://user-images.githubusercontent.com/119637398/228755834-42fbc927-ca07-4e33-982c-c6ad292daf54.jpg">  

- jenkins의 기본 포트는 8080이므로 변경 필요.
  - jenkins 종료
  ```
  sudo service jenkins stop
  ```
  - jenkins 포트변경 및 변경할 포트의 방화벽 오픈
  ```
  sudo vi /usr/lib/systemd/system/jenkins.service
  ```
  <img src="https://user-images.githubusercontent.com/119637398/228755839-8ab78713-72e7-4e09-a01c-0090c0ead61e.jpg">  
  
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
<img src="https://user-images.githubusercontent.com/119637398/228755837-0e2da744-34a7-46db-8414-e09886eff8ac.jpg">  

