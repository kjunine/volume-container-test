Volume Container Test
=====================

### Boot2docker 실행

```
$ boot2docker up
```

### Volume Container 빌드, 실행 및 확인

```
$ cd data
$ docker build -t kjunine/data .
$ docker run --name data kjunine/data
$ docker ps -a
```

### App Container 빌드 및 실행

```
$ cd app
$ docker build -t kjunine/app .
$ docker run -it --volumes-from data --name app kjunine/app /bin/bash
$ ls -al
$ exit
```

### App Container 안에서

```
# df -h
# cd /data
# git clone https://github.com/octocat/Spoon-Knife.git
```

### Container 삭제

```
$ docker ps -a
$ docker rm data app
$ docker ps -a
```

### Volume Container 내용 확인

```
$ boot2docker ssh
$ cd /var/lib/docker
$ sudo ls -al vfs/dir
$ sudo ls -al vfs/dir/`sudo ls vfs/dir`
$ sudo ls -al vfs/dir/`sudo ls vfs/dir`/Spoon-Knife
```
