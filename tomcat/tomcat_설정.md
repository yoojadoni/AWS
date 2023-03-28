
#### 1. tomcat 다운로드 및 압축 해제
```
wget http://archive.apache.org/dist/tomcat/tomcat-9/v9.0.4/bin/apache-tomcat-9.0.4.tar.gz
tar -xvf apache-tomcat-9.0.4.tar.gz
```

#### 2. tomcat 설치
tomcat 폴더 생성
```
sudo mkdir /home/ec2-user/tomcat
```
관리의 편의성을 위해 해당 위치에 생성(해당 폴더의 위치는 개인적 의견일뿐입니다.)

#### 3. tomcat 실행
```
/home/ec2-user/tomcat/apache-tomcat-9.0.4/bin/startup.sh
```
<img src="https://user-images.githubusercontent.com/119637398/228101069-51d93145-4124-45f2-a967-fa13f00b429a.jpg">

#### 4. tomcat 포트 확인 및 연결확인
```
netstat -an | grep 8080
```
브라우저에 http://IP:8080으로 접속 확인.  
<img src="https://user-images.githubusercontent.com/119637398/228101073-cf67a0a6-ae2c-4e1f-a9c1-9fdda6ba4caf.jpg">
