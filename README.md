# Docker Oracle Database 12c Release 2
Setting Docker Oracle Database 12c Release 2

Download Oracle Database 12c Release 2
https://www.oracle.com/database/technologies/oracle-database-software-downloads.html

Download Java SE Development Kit 8
https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

$ git clone https://github.com/oracle/docker-images.git

Copy file linuxx64_12201_database.zip
Path :: docker-images/OracleDatabase/SingleInstance/dockerfiles/12.2.0.1

Docker => preference => Daemon => Advanced
add :: "dns" : [ "8.8.8.8", "8.8.4.4" ]

$ cd docker-images/OracleDatabase/SingleInstance/dockerfiles
$ ls -lrt
$ ./buildDockerImage.sh -v 12.2.0.1 -s -i
$ docker images |grep oracle
$ docker login -u username -p password
$ docker run --name OracleSE \
-p 1521:1521 -p 5500:5500 \
-e ORACLE_SID=TEST01 \
-e ORACLE_PDB=TESTPDB01 \
-e ORACLE_PWD=password \
-e ORACLE_CHARACTERSET=AL32UTF8 \
oracle/database:12.2.0.1-se2

$ docker ps

tools : datagrip , sql developer

Remove docker images
$ sudo docker ps -as
$ sudo docker rmi <IMAGE_ID> -f

Remove unused data
$ docker system prune
