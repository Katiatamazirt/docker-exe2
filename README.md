# docker-exe2
## faire un clone local
git clone https://github.com/Katiatamazirt/docker-exe2.git
## faire un clone dans la vm avec les intruction de l'exercice
git clone https://github.com/Katiatamazirt/docker-exe2.git
## commencer l'exercice en executant le dockerfile que je viens de rajouter de mon répertoire 
cd docker-exe2
## ------dossier dockerfile est : 
FROM fabric8/tomcat-9
RUN sudo apt update && \
COPY webapp.war /opt/tomcat/webapps/webapp.war
## execution du dossier dockerfile
docker build -t tomcat:v1 .
## virification de la création de l'image
docker images nom-image <tomcat:v1> et ID <6788a746cb50>

docker history 
### nous retourne le port 8080 pour tomcat
<missing>   2 years ago  /bin/sh -c #(nop)  EXPOSE 8778 9779    0B 
<missing>   2 years ago  /bin/sh -c #(nop)  EXPOSE 8080   0B

docker inspect 6788a746cb50
## nous retourne
"8080/tcp": {},
## docker run pour creer un container
docker run -d --name tomcat-container -p 20200:8080 tomcat:v1
## verification avec 
docker exec -it tomcat-container /bin/bash
cd /opt/tomcat/conf/
vi tomcat-users.xml
## --<user name="logwire" password="docker" roles="admin-gui,admin-script,manager-gui,manager-status,manager-script,manager-jmx"/> </tomcat-users>
## pousser l'image tomcat:v1 vers dockerhub
docker image tag tomcat:v1 katiatamazirt/tag tomcat:v1
docker push katiatamazirt/tag tomcat:v1
## mettre mon dossier dans github
2 git config --global user.email katiatamazirt@hotmail.com
3 git config --global user.name katiatamazirt
git add Dockerfile
git add webapp.war
6 git commit -am"solution exo02"
7 git push origin main