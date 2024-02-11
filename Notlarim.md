```bash
docker run hello-world        

"Hello from Docker!"
- This message shows that your installation appears to be working correctly.
```

```bash
docker run -i -t ubuntu bash
cat /etc/os-release
echo $0       - Display the shell name on the container for the current user.
apt-get update && apt-get upgrade -y   - Update and upgrade os packages on `ubuntu` container.

```
```bash
docker run ubuntu ls
docker run ubuntu whoami

```

- Her docker run komutunu girdigimizde yeni bir container olusturur.
-ps komutu ile linux'teki processleri gorursun. 

### docker container ls -a 
CONTAINER ID   IMAGE         COMMAND    CREATED             STATUS                         PORTS     NAMES
29fdfb76819c   ubuntu        "ls"       2 minutes ago       Exited (0) 2 minutes ago                 gallant_brown
1c5bffbb6492   hello-world   "/hello"   About an hour ago   Exited (0) About an hour ago             optimistic_shamir
e6ae86bb7d18   ubuntu        "bash"     2 hours ago         Exited (0) 2 hours ago                   compassionate_swartz
87a6c1366c5c   ubuntu        "bash"     2 hours ago         Up About an hour                         upbeat_gould

### docker ps -a
CONTAINER ID   IMAGE         COMMAND    CREATED             STATUS                         PORTS     NAMES
29fdfb76819c   ubuntu        "ls"       3 minutes ago       Exited (0) 3 minutes ago                 gallant_brown
1c5bffbb6492   hello-world   "/hello"   About an hour ago   Exited (0) About an hour ago             optimistic_shamir
e6ae86bb7d18   ubuntu        "bash"     2 hours ago         Exited (0) 2 hours ago                   compassionate_swartz
87a6c1366c5c   ubuntu        "bash"     2 hours ago         Up About an hour                         upbeat_gould

### docker ps 
CONTAINER ID   IMAGE     COMMAND   CREATED       STATUS             PORTS     NAMES
87a6c1366c5c   ubuntu    "bash"    2 hours ago   Up About an hour             upbeat_gould



```bash
docker run -it alpine ash
cat /etc/os-release
cd home && touch short-life.txt && ls
exit
```

--volume <volume-name>:<path>:<list-of-options> 
- path: container'da nereye baglayacagin. Mesela /app 
- list_of_options: Mesela bunu read-only yapabiliyoruz. 

```bash
docker run -dit -v myvolume:/app nginx
```

- Volume her zaman baskindir. 

## Part 5 - docker volume behaviours

|No | Situation   | Behaviour |
| ---- | ----------- | ------------ |
| 1    | If there is no target directory. | The target directory is created and files inside volume are copied to this directory. |
| 2    | If there is target directory, but it is empty. | The files in volume are copied to target directory.  |
| 3    | If there is target directory and it is not empty, but volume is empty. | The files in the target directory are copied to volumes. |
| 4    | If the volume is not empty. | There will be just the files inside the volume regardless of the target directory is full or empty. |


## Network

Uc adet default network drivers var.
- Default
- Host
- Bridge 1)docker0 2)user defined

- -p host_port:container_port 

- Aksi belirtilmedikce default olarak containerlar'i bridge network'e baglar.