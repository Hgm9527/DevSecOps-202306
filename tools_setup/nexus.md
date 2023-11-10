
https://www.devopsschool.com/blog/sonatype-nexus-installation-using-docker/

docker run --name nexus -d -p 8081:8081  sonatype/nexus:oss

http://15.206.171.77:8081/nexus/



How to Install Sonatype Nexus installation using Docker?
RAJESH KUMAR FEBRUARY 23, 2016 COMMENTS OFF
sonatype-nexus-installation-using-docker
Sonatype Nexus Repository Manager 2
Install a Docker Engine
Installation Instructions can be found here – http://www.devopsschool.com/tutorial/docker/docker-install-and-configuration.html

Download a Sonatype Nexus Image
> docker pull sonatype/nexus

For Sonatype Nexus Repository Manager 2 OSS, To run (if port 8081 is open on your host):
> docker run -d -p 8081:8081 --name nexus sonatype/nexus:oss

For Sonatype Nexus Repository Manager 2 PRO, To run (if port 8081 is open on your host):
> docker run -d -p 8082:8081 --name nexuspro sonatype/nexus:pro

To determine the port that the container is listening on:
> docker ps -l

To Test
> curl http://localhost:8081/nexus/service/local/status

Browse Following URL
http://localhost:8081/nexus/

It can take some time (2-3 minutes) for the service to launch in a new container. You can tail the log to determine once Nexus is ready:
> docker logs -f nexus

Note
Default credentials are: admin / admin123
Installation of Nexus is to /opt/sonatype/nexus
Notably: /opt/sonatype/nexus/conf/nexus.properties is the properties file.
Parameters (nexus-work and nexus-webapp-context-path) defined
here are overridden in the JVM invocation.

Sonatype Nexus Repository Manager 3
Install a Docker Engine
Installation Instructions can be found here – http://www.devopsschool.com/tutorial/docker/docker-install-and-configuration.html

Clone the Repostory from Gihub
> git clone https://github.com/sonatype/docker-nexus3
> cd docker-nexus3

Build a Image for Sonatype Nexus Repository Manager 3 OSS
> docker build –rm –tag sonatype/nexus oss/

Build a Image for Sonatype Nexus Repository Manager 3 PRO
> docker build –rm –tag sonatype/nexus:pro pro/

For Sonatype Nexus Repository Manager 2 OSS, To run (if port 8081 is open on your host):
> docker run -d -p 8081:8081 –name nexus sonatype/nexus:oss

For Sonatype Nexus Repository Manager 2 PRO, To run (if port 8081 is open on your host):
> docker run -d -p 8081:8081 –name nexus sonatype/nexus:pro

To determine the port that the container is listening on:
> docker ps -l

To Test
> curl http://localhost:8081/nexus/service/local/status

Browse Following URL
http://localhost:8081/nexus/

It can take some time (2-3 minutes) for the service to launch in a new container. You can tail the log to determine once Nexus is ready:
> docker logs -f nexus

Note
Default credentials are: admin / admin123
Installation of Nexus is to /opt/sonatype/nexus
Notably: /opt/sonatype/nexus/conf/nexus.properties is the properties file.
Parameters (nexus-work and nexus-webapp-context-path) defined
here are overridden in the JVM invocation.