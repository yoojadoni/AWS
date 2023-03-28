### 1. nginx 설정 파일 수정.
```
sudo vi /etc/nginx/conf.d/default.conf
```
아래와 같이 파일수정  
<img src="https://user-images.githubusercontent.com/119637398/228102221-ae719182-ac71-4d3f-bd4f-7dfb414f3229.jpg">

### 2. nginx 재시작
```
sudo systemctl restart nginx
```

### 3. nginx-tomcat 연동확인
- 브라우저에 포트번호 없이 IP주소로만 접속
- nginx화면이 아닌 Tomcat화면이 나오면 <strong>정상</strong>  
<img src="https://user-images.githubusercontent.com/119637398/228102917-fe347912-1a96-46ac-b81b-cfc784418cdf.png"
 width="100%" height="50%">
