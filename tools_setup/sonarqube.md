https://www.heyvaldemar.com/install-sonarqube-with-docker-compose/

https://www.heyvaldemar.com/install-docker-engine-and-docker-compose-on-ubuntu-server/


https://github.com/heyValdemar/sonarqube-traefik-letsencrypt-docker-compose/blob/main/sonarqube-traefik-letsencrypt-docker-compose.yml


```
apt install unzip
adduser sonarqube
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-9.4.0.54424.zip
unzip *
chmod -R 755 /home/sonarqube/sonarqube-9.4.0.54424
chown -R sonarqube:sonarqube /home/sonarqube/sonarqube-9.4.0.54424
cd sonarqube-9.4.0.54424/bin/linux-x86-64/
./sonar.sh start
```

