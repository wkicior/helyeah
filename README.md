# helyeah
Main helyeah repository
# docker start wwo-proxy
$ docker run -d --name wwo-proxy -p 8000:80 wkicior/wwo-proxy:v3

$ docker run -d --name mail-gateway --privileged=true -v /home/disorder/praca/helyeah/mail-gateway:/app:rw -p 9998:80 wkicior/mail-gateway

$ docker run --name notifications-mongo -d mongo

$ docker run -d --privileged=true --name notifications-service --link mail-gateway:mail-gateway --link notifications-mongo:notifications-mongo -v /home/disorder/praca/helyeah/notifications-service:/app:rw -p 9999:9000 wkicior/notifications-service

$ docker run --privileged=true -i -t -p 8091:8020 --link notifications-service:notifications --link wwo-proxy:wwo-proxy -v /home/disorder/.m2:/root/.m2 wkicior/forecast-engine


wget http://localhost:8091/app/resources/forecast-engine/12/13
