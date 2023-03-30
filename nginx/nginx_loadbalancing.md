### Nginx loadbalancing

- loadbalancing 알고리즘
  - Round Robin  
    기본 알고리즘으로 아무 설정도 하지 않으면 기본으로 라운드 로빈 알고리즘으로 로드 밸런싱이 진행된다.
  - Least Connections  
    연결된 횟수가 가장 적은 서버로 연결되는 알고리즘이다.
  - IP Hash  
    클라이언트 IP를 해싱하여 특정 클라이언트는 특정 서버로 연결되게 할 수 있다. Stick Session 세션 방식 처럼 동작하게 할 수 있다.
  - Generic Hash  
    사용자가 정의한 다양한 변수를 조합해 트래픽을 분산할 수 있다.
    
  기타 자세한건 공식문서 참고(https://docs.nginx.com/nginx/admin-guide/load-balancer/http-load-balancer/)

#### 설정파일 변경
```
sudo vi /etc/nginx/conf.d/default.conf
```

```
upstream server {
  #load balancing 알고리즘 작성
  #default Round Robin
  #least_conn;
  #ip_hash;
  server localhost:8080;
  server localhost:9090;
}

server {
    listen       80;
    server_name  localhost;

    #access_log  /var/log/nginx/host.access.log  main;

    location / {
         #        root   /usr/share/nginx/html;
        index  index.html index.htm;
        proxy_pass http://server;
    }
}
```

- 테스트를 위한 세팅 
  - application.yml에 프로파일 2개작성
  - 구동된 서버의 port 및 서버정보 확인 가능한 API 구축.
  - nohup java -jar -Dspring.profiles.active=server1 파일명 &
  - nohup java -jar -Dspring.profiles.active=server2 파일명 &
  - netstat -lntp로 서버 구동 확인.

#### 아래와 같이 로드밸런싱된 내역 확인가능.

<img src="https://user-images.githubusercontent.com/119637398/228784602-e4f18719-d2a7-4db5-a2eb-0f0dfb4d451c.jpg"/>
<img src="https://user-images.githubusercontent.com/119637398/228784611-0eb66b95-2402-4ec4-ac8e-bd84846397ef.jpg"/>
