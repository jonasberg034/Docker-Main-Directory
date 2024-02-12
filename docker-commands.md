> docker run <image-name>
> docker run -dit ubuntu bash
> docker run -dit --name clarus ubuntu bash
> docker run ubuntu ls
> docker run ubuntu whoami
> docker run ubuntu sleep 10
> docker run -dit alpine ash
> docker run -dit --name clarus clarusway/hello-clarus sh
> docker container run --rm -d -p 8080:80 --name ng nginx
- -rm parametresi ile isi bittiginde sil demek. Yani container stop edince siler. Bu komuttan sonra docker stop de ve dene.

> docker run -d -p 80:80 nginx
-detached modda calisacak 80 portu publish edecek
> docker run -d -p 8080:80 httpd 

> docker ps ve docker container ls 
> docker container ls -a   
> docker ps -a
- Show the list of all containers available on Docker machine and explain container properties.
- a ile running ve stop olan containerlarda gozukur.
- docker ps ve docker container ls ile sadece calisan containerlari goruruz.

> docker container ls -aq
- Sadece ID leri lsiteler

> docker start <container-name> 
> docker exec -it <container-name> <bash-veya-baska-ne-ise>
- exec komutunu calistigini gormek icin container satart edilmesi lazim.

> docker rm <container-name>
> docker container prune 
- Remove all stopped containers, Prune budamaktan geliyor

> docker rm -f $(docker ps -aq)
- Tum containerlari siler

> docker images ve docker image ls
- Ayni komut bunlar!
> docker image pull ubuntu
> docker run -it ubuntu


> docker container inspect <container-id>
> docker container inspect clarus2nd | grep IPAddress
> docker image inspect <image-id>

> docker exec <container-id> ls
> docker exec -it bb4 bash
> cd /usr/share/nginx/html/   ---> echo "hi" > index.html

> docker run -dit -v myvolume:/app nginx
> docker volume create cw-vol
> docker volume ls
> docker volume inspect cw-vol
> sudo ls -al  /var/lib/docker/volumes/cw-vol/_data
> docker run -it --name clarus -v cw-vol:/cw alpine ash
> docker run -it --name clarus4th -v cw-vol:/cw4th:ro ubuntu bash  
- read only bir volume olusturduk.

```bash
mkdir webpage && cd webpage
echo "<h1>Welcome to Clarusway</h1>" > index.html
```
> docker run -d --name nginx-new -p 8080:80 -v /home/ec2-user/webpage:/usr/share/nginx/html nginx
- webpage dizini altindaki index.html dosyasini, container icindeki tarif edilen dizine baglar. 
- -p host_port:container_port

```bash
cd /home/ec2-user/webpage
echo "<h2>This is added for docker volume lesson</h2>" >> index.html
```
-Bunun sonucunda ikinici satira usttekini ekler. 

> docker network ls
> docker network inspect bridge | less    - less tum sayfayi alma demek
> docker network 

```bash
docker container run -dit --name clarus1st alpine ash
docker container run -dit --name clarus2nd alpine ash
```
> docker exec -it clarus1st ash
```bash
ifconfig
```
```bash
ping -c 4 google.com
```
> docker network create --driver bridge 
> docker container run -dit --network clarusnet --name clarus1st alpine ash
> docker container run -dit --network clarusnet --name clarus2nd alpine ash
- Bu iki container user-defined network'e de baglanmis oluyor. Bu yuzden ismi ile ping atip baglanabilirisn. Ancak clarus3rd user-defined degildir. Default oarak bridge network'e baglandigi icin. 
> docker container run -dit --name clarus3rd alpine ash
> docker container run -dit --name clarus4th alpine ash
> docker network connect clarusnet clarus4th      
- clarus4th container'i clarusnet agina baglar. Ama ayni zamanda default bridge aginda da olur. user-defined olur.

> docker build -t "clarusway/flask-app:1.0" .
> docker build -t "clarusway/flask-app:2.0" -f ./Dockerfile-alpine .
> docker run -d --name welcome -p 80:80 clarusway/flask-app:1.0
> docker search ubuntu
- Dockerhub'ta ubuntu imajlarani search ediyor.
> docker login
> docker push clarusway/flask-app:1.0

> docker compose up -d --build 
- Guncelledigin Dockerfile'i guncellemek icin kullanilan komut. 
