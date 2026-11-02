### 1. Ubuntu Terminal 기본 조작 로그

pwd                     # 현재 위치
ls -al                  # 숨김파일 포함 목록
mkdir testdir           # 디렉토리 생성
touch test.txt          # 빈 파일 생성
cp test.txt copy.txt    # 복사
mv copy.txt renamed.txt # 이름변경/이동
echo "hello" > test.txt # 내용 쓰기
cat test.txt            # 내용 확인
rm renamed.txt          # 삭제

```
yhmin@yhforwindows:~$ pwd
/home/yhmin
yhmin@yhforwindows:~$ ls -al
total 56
drwxr-x--- 9 yhmin yhmin 4096 Nov  1 22:35 .
drwxr-xr-x 3 root  root  4096 Nov  1 21:48 ..
lrwxrwxrwx 1 yhmin yhmin   23 Nov  1 22:13 .aws -> /mnt/c/Users/nan04/.aws
lrwxrwxrwx 1 yhmin yhmin   25 Nov  1 22:13 .azure -> /mnt/c/Users/nan04/.azure
-rw------- 1 yhmin yhmin  161 Nov  1 22:35 .bash_history
-rw-r--r-- 1 yhmin yhmin  220 Nov  1 21:48 .bash_logout
-rw-r--r-- 1 yhmin yhmin 3771 Nov  1 21:48 .bashrc
drwxr-x--- 6 yhmin yhmin 4096 Nov  1 22:25 .cache
drwxr-x--- 3 yhmin yhmin 4096 Nov  1 21:48 .config
drwx------ 4 yhmin yhmin 4096 Nov  1 22:30 .copilot
drwxr-xr-x 4 yhmin yhmin 4096 Nov  1 22:13 .docker
drwxr-xr-x 3 yhmin yhmin 4096 Nov  1 22:25 .dotnet
-rw-rw-r-- 1 yhmin yhmin    0 Nov  1 21:48 .motd_shown
-rw-r--r-- 1 yhmin yhmin  807 Nov  1 21:48 .profile
drwxr-xr-x 5 yhmin yhmin 4096 Nov  1 22:25 .vscode-server
-rw-r--r-- 1 yhmin yhmin  183 Nov  1 22:25 .wget-hsts
drwxr-xr-x 4 yhmin yhmin 4096 Nov  1 22:24 workstation
yhmin@yhforwindows:~$ mkdir testdir
yhmin@yhforwindows:~$ touch test.txt
yhmin@yhforwindows:~$ cp test.txt copy.txt
yhmin@yhforwindows:~$ copy.yxy renamed.txt
copy.yxy: command not found
yhmin@yhforwindows:~$ mv copy.txt renamed.txt
yhmin@yhforwindows:~$ echo "hello" > test.txt
yhmin@yhforwindows:~$ cat test.txt
hello
yhmin@yhforwindows:~$ rm renamed.txt
yhmin@yhforwindows:~$
```

<hr/>

### 2. Ubuntu 권한 실습(파일1 + 디렉토리1)

ls -l test.txt          # [전] 권한 확인
chmod 644 test.txt
ls -l test.txt          # [후] 권한 확인

ls -ld testdir          # [전]
chmod 755 testdir
ls -ld testdir          # [후]


```
yhmin@yhforwindows:~$ ls -1 test.txt
test.txt
yhmin@yhforwindows:~$ chmod 644 test.txt
yhmin@yhforwindows:~$ ls -l.txt
error: unexpected argument '-.' found

  tip: to pass '-.' as a value, use '-- -.'

Usage: ls [OPTION]... [FILE]...

For more information, try '--help'.
yhmin@yhforwindows:~$ ls -l test.txt
-rw-r--r-- 1 yhmin yhmin 6 Nov  1 22:39 test.txt
** yhmin@yhforwindows:~$ ls -ld testdir **
drwxr-xr-x 2 yhmin yhmin 4096 Nov  1 22:36 testdir
yhmin@yhforwindows:~$ chmod 755 testdir
yhmin@yhforwindows:~$ ls -ld testdir
drwxr-xr-x 2 yhmin yhmin 4096 Nov  1 22:36 testdir
yhmin@yhforwindows:~$

```

r=4, w=2, x=1 / 755 = 소유자7·그룹5·기타5

<hr/>

### 3. Docker 점검, 기본 운영

docker --version        # 버전
docker info             # 데몬 동작 확인
docker run hello-world  # 동작 테스트
docker images           # 이미지 목록
docker ps -a            # 컨테이너 목록

```
yhmin@yhforwindows:~$ docker --version
Docker version 29.9.2, build a82e528

yhmin@yhforwindows:~$ docker info
Client:
 Version:    29.9.2
 Context:    default
 Debug Mode: false
 Plugins:
  agent: Docker AI Agent Runner (Docker Inc.)
    Version:  v1.152.0
    Path:     /usr/local/lib/docker/cli-plugins/docker-agent
  ai: Docker AI Agent - Ask Gordon (Docker Inc.)
    Version:  v1.33.0
    Path:     /usr/local/lib/docker/cli-plugins/docker-ai
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.38.1
    Path:     /usr/local/lib/docker/cli-plugins/docker-buildx
  compose: Docker Compose (Docker Inc.)
    Version:  v5.6.1
    Path:     /usr/local/lib/docker/cli-plugins/docker-compose
  debug: Get a shell into any image or container (Docker Inc.)
    Version:  0.49.0
    Path:     /usr/local/lib/docker/cli-plugins/docker-debug
  desktop: Docker Desktop commands (Docker Inc.)
    Version:  4.97.0
    Path:     /usr/local/lib/docker/cli-plugins/docker-desktop
  dhi: CLI for managing Docker Hardened Images (Docker Inc.)
    Version:  v0.0.9
    Path:     /usr/local/lib/docker/cli-plugins/docker-dhi
  extension: Manages Docker extensions (Docker Inc.)
    Version:  v0.2.32
    Path:     /usr/local/lib/docker/cli-plugins/docker-extension
  init: Creates Docker-related starter files for your project (Docker Inc.)
    Version:  v1.4.1
    Path:     /usr/local/lib/docker/cli-plugins/docker-init
  mcp: Docker MCP Plugin (Docker Inc.)
    Version:  v0.44.2
    Path:     /usr/local/lib/docker/cli-plugins/docker-mcp
  model: Docker Model Runner (Docker Inc.)
    Version:  v1.2.9
    Path:     /usr/local/lib/docker/cli-plugins/docker-model
  offload: Docker Offload (Docker Inc.)
    Version:  v0.7.21
    Path:     /usr/local/lib/docker/cli-plugins/docker-offload
  pass: Docker Pass Secrets Manager Plugin (beta) (Docker Inc.)
    Version:  v0.3.2
    Path:     /usr/local/lib/docker/cli-plugins/docker-pass
  sandbox: "docker sandbox" is deprecated, use Docker Sandboxes instead (Docker Inc.)
    Version:  v0.13.0
    Path:     /usr/local/lib/docker/cli-plugins/docker-sandbox
  scout: Docker Scout (Docker Inc.)
    Version:  v1.27.0
    Path:     /usr/local/lib/docker/cli-plugins/docker-scout
Server:
 Containers: 0
  Running: 0
  Paused: 0
  Stopped: 0
 Images: 0
 Server Version: 29.9.2
 Storage Driver: overlayfs
  driver-type: io.containerd.snapshotter.v1
 Logging Driver: local
 Cgroup Driver: cgroupfs
 Cgroup Version: 2
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
 CDI spec directories:
  /etc/cdi
  /var/run/cdi
 Discovered Devices:
  cdi: docker.com/gpu=webgpu
 Swarm: inactive
 Runtimes: io.containerd.runc.v2 nvidia runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: b7a25261e029d68978bbf290df0a62fc819b3c51
 runc version: v1.5.2-0-g29dd3dc2
 init version: de40ad0
 Security Options:
  seccomp
   Profile: builtin
  cgroupns
 Kernel Version: 6.18.54.1-microsoft-standard-WSL2
 Operating System: Docker Desktop
 OSType: linux
 Architecture: x86_64
 CPUs: 18
 Total Memory: 7.514GiB
 Name: docker-desktop
 ID: c5cb5511-5e09-4bd7-830c-68041eafaaf8
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 HTTP Proxy: http.docker.internal:3128
 HTTPS Proxy: http.docker.internal:3128
 No Proxy: hubproxy.docker.internal
 Labels:
  com.docker.desktop.address=unix:///var/run/docker-cli.sock
 Experimental: false
 Insecure Registries:
  hubproxy.docker.internal:5555
  127.0.0.0/8
  ::1/128
 Live Restore Enabled: false
 Firewall Backend: iptables


yhmin@yhforwindows:~$ docker run hello-world
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/


yhmin@yhforwindows:~$ docker images
                         i Info →   U  In Use
IMAGE               ID             DISK USAGE
hello-world:latest
                    c567b231f656       25.9kB

yhmin@yhforwindows:~$ docker ps -a
CONTAINER ID   IMAGE         COMMAND    CREATED          STATUS                      PORTS     NAMES
903488522f8f   hello-world   "/hello"   36 seconds ago   Exited (0) 36 seconds ago             interesting_goodall
65df614df491   hello-world   "/hello"   2 minutes ago    Exited (0) 2 minutes ago              serene_chaplygin

```
- Ubuntu 컨테이너 진입
docker run -it ubuntu bash
   (컨테이너 안에서)
ls
echo "hello from container"
exit

```
yhmin@yhforwindows:~$ docker run -it ubuntu bash
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
f3f25b84a7d7: Pull complete
edafa32f5d9e: Pull complete
21594acc2d8b: Download complete
Digest: sha256:6a06111c3b0a8600feadb270aec771dc239bf407b25625f93f44ab00e11f4d3c
Status: Downloaded newer image for ubuntu:latest
root@06f1742ac3f3:/# ls
bin   etc   lib64  opt   run   sys  var
boot  home  media  proc  sbin  tmp
dev   lib   mnt    root  srv   usr
root@06f1742ac3f3:/# echo "hello from container"
hello from container
root@06f1742ac3f3:/#
```
exit(종료) 와 exec(유지)

<hr/>

### 4. Dockerfile 커스텀 웹 서버
**1. app/index.html 작성**
```
yhmin@yhforwindows:~/workstation$ mkdir -p app
yhmin@yhforwindows:~/workstation$ cat > app/index.html <<'EOF'
> <h1>My Docker Web Server</h1>
> <p>안녕하세요! 커스텀 이미지입니다.</p>
> EOF
```
**2. Dockerfile 작성 (workstation 폴더)**
```
yhmin@yhforwindows:~/workstation$ cat > Dockerfile << 'EOF'
> FROM nginx:latest
> COPY app/index.html /usr/share/nginx/html/i
ndex.html
> EOF
yhmin@yhforwindows:~/workstation$ cat Dockerfile
FROM nginx:latest
COPY app/index.html /usr/share/nginx/html/index.html
```

**3. 빌드 & 실행**
```
yhmin@yhforwindows:~/workstation$ docker build -t my-web .
[+] Building 12.5s (7/7) FINISHED docker:defa
 => [internal] load build definition f  0.0s
 => => transferring dockerfile: 108B    0.0s
 => [internal] load metadata for docke  2.9s
 => [internal] load .dockerignore       0.0s
 => => transferring context: 2B         0.0s
 => [internal] load build context       0.1s
 => => transferring context: 152B       0.0s
 => [1/2] FROM docker.io/library/nginx  7.9s
 => => resolve docker.io/library/nginx  0.0s
 => => sha256:6e2ab1f3ef4e 964B / 964B  0.2s
 => => sha256:9f604dae09b2 628B / 628B  0.4s
 => => sha256:d322f1bf 1.21kB / 1.21kB  0.6s
 => => sha256:a670537b 1.40kB / 1.40kB  0.6s
 => => sha256:c139fe92686d 404B / 404B  0.4s
 => => sha256:a07111 34.05MB / 34.05MB  4.4s
 => => sha256:6fc242 29.86MB / 29.86MB  5.8s
 => => extracting sha256:6fc242d221a67  0.6s
 => => extracting sha256:a071113ac5751  0.5s
 => => extracting sha256:9f604dae09b21  0.0s
 => => extracting sha256:6e2ab1f3ef4e0  0.0s
 => => extracting sha256:c139fe92686de  0.0s
 => => extracting sha256:d322f1bf41d8e  0.0s
 => => extracting sha256:a670537bed708  0.0s
 => [2/2] COPY app/index.html /usr/sha  0.2s
 => exporting to image                  1.3s
 => => exporting layers                 0.1s
 => => exporting manifest sha256:ab898  0.0s
 => => exporting config sha256:e15febd  0.0s
 => => exporting attestation manifest   0.0s
 => => exporting manifest list sha256:  0.0s
 => => naming to docker.io/library/my-  0.0s
 => => unpacking to docker.io/library/  1.1s
yhmin@yhforwindows:~/workstation$ docker run -d -p 8080:80 --name web1 my-web
01ddaf6927f63e4581a3ceb88f63fea5209b9098f9744ce00f85f64c32c7137b
yhmin@yhforwindows:~/workstation$ docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS         PORTS                                     NAMES
01ddaf6927f6   my-web    "/docker-entrypoint.…"   11 seconds ago   Up 9 seconds   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   web1
yhmin@yhforwindows:~/workstation$ docker logs web1
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2026/11/01 14:19:17 [notice] 1#1: using the "epoll" event method
2026/11/01 14:19:17 [notice] 1#1: nginx/1.31.8
2026/11/01 14:19:17 [notice] 1#1: built by gcc 14.2.0 (Debian 14.2.0-19)
2026/11/01 14:19:17 [notice] 1#1: OS: Linux 6.18.54.1-microsoft-standard-WSL2
2026/11/01 14:19:17 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2026/11/01 14:19:17 [notice] 1#1: start worker processes
2026/11/01 14:19:17 [notice] 1#1: start worker process 29
2026/11/01 14:19:17 [notice] 1#1: start worker process 30
2026/11/01 14:19:17 [notice] 1#1: start worker process 31
2026/11/01 14:19:17 [notice] 1#1: start worker process 32
2026/11/01 14:19:17 [notice] 1#1: start worker process 33
2026/11/01 14:19:17 [notice] 1#1: start worker process 34
2026/11/01 14:19:17 [notice] 1#1: start worker process 35
2026/11/01 14:19:17 [notice] 1#1: start worker process 36
2026/11/01 14:19:17 [notice] 1#1: start worker process 37
2026/11/01 14:19:17 [notice] 1#1: start worker process 38
2026/11/01 14:19:17 [notice] 1#1: start worker process 39
2026/11/01 14:19:17 [notice] 1#1: start worker process 40
2026/11/01 14:19:17 [notice] 1#1: start worker process 41
2026/11/01 14:19:17 [notice] 1#1: start worker process 42
2026/11/01 14:19:17 [notice] 1#1: start worker process 43
2026/11/01 14:19:17 [notice] 1#1: start worker process 44
2026/11/01 14:19:17 [notice] 1#1: start worker process 45
2026/11/01 14:19:17 [notice] 1#1: start worker process 46
```

<hr/>

### 4. 포트 매핑 2회 접속
#### 1회차 (이미 web1이 8080에서 실행 중)
```curl http://localhost:8080```
- curl: 웹 주소에 접속해서 응답 내용을 터미널에 보여주는 명령어
```yhmin@yhforwindows:~/workstation$ curl http://localhost:8080```

#### 2회차 (포트 바꿔서 하나 더)
```docker run -d -p 8081:80 --name web2 my-web
curl <http://localhost:8081>```

```yhmin@yhforwindows:~/workstation$ docker run -d -p 8081:80 --name web2 my-web
31a182b1237761e0cb45bbf3ff83b991e821e357c49b81c6fa969f5311f4d8ce
yhmin@yhforwindows:~/workstation$ curl http://localhost:8081
<h1>My Docker Web Server</h1>
<p>안녕하세요! 커스텀 이미지입니다.</p>
yhmin@yhforwindows:~/workstation$
```

<hr/>

### 5. 바인드 마운트 실습 

- **호스트의 app 폴더를 컨테이너에 직접 연결**
```
yhmin@yhforwindows:~/workstation$ docker run -d -p 8082:80 -v $(pwd)/app:/usr/share/nginx/html --name web3 my-web
272b20ab47c8d06d37bb07130034bbda86d24e1f3a37aa0badbda8e170cfcdef
yhmin@yhforwindows:~/workstation$ curl http://localhost:8082
<h1>My Docker Web Server</h1>
<p>안녕하세요! 커스텀 이미지입니다.</p>
yhmin@yhforwindows:~/workstation$

```
- **VSCode에서 app/index.html 수정 후 변경 내용 확인**

```
yhmin@yhforwindows:~/workstation$ curl http://localhost:8082
<h1>My Docker Web Server</h1>
<p>안녕하세요! 커스텀 이미지입니다.</p>
<p>index.html을 수정 해봤습니다.</p>
```
- **바인드 마운트 = 내 PC 폴더를 직접 연결 → 실시간 반영**

- <hr/>

### 6. 볼륨 영속성 검증
#### 볼륨 생성
docker volume create mydata

```
yhmin@yhforwindows:~/workstation$ docker volume create mydata
mydata
```

#### 볼륨 연결 후 데이터 저장
docker run -it -v mydata:/data --name voltest ubuntu bash
echo "저장된 데이터" > /data/file.txt
cat /data/file.txt
exit

```
yhmin@yhforwindows:~/workstation$ docker volume create mydata
mydata
yhmin@yhforwindows:~/workstation$ docker rum -it -v mydata:/data --name voltest ubuntu bash
unknown shorthand flag: 'i' in -it

Usage:  docker [OPTIONS] COMMAND [ARG...]

Run 'docker --help' for more information
yhmin@yhforwindows:~/workstation$ docker run
-it -v mydata:/data --name voltest ubuntu bas
h
root@2bbb9e6e74fb:/# echo "saved data" > /data/file.txt
root@2bbb9e6e74fb:/# cat /data/file.txt
saved data
root@2bbb9e6e74fb:/# exit
exit

```

#### 컨테이너 삭제
docker rm voltest

```
yhmin@yhforwindows:~/workstation$ docker rm voltest
voltest
```

#### 새 컨테이너에 같은 볼륨 연결 → 데이터 확인
docker run -it -v mydata:/data ubuntu bash
cat /data/file.txt          # 데이터가 그대로면 성공!
exit

```
yhmin@yhforwindows:~/workstation$ docker run -it -v mydata:/data ubun
tu bash
root@b5d990671e0c:/# cat /data/file.txt
saved data
root@b5d990671e0c:/# exit
exit
```

- 볼륨 = Docker가 관리하는 저장소 → 컨테이너 삭제돼도 데이터 유지

- <hr/>

### 7. Git 설정 & GitHub 연동

**1. Git 설정**
```
**yhmin@yhforwindows:~/workstation$ git config --global user.name "nan041768-ui"**
**yhmin@yhforwindows:~/workstation$ git config --global user.email "nan041768@gmail.com"**
**yhmin@yhforwindows:~/workstation$ git config --global init.defaultBranch main**
yhmin@yhforwindows:~/workstation$ git config --list
user.name=nan041768-ui
user.email=nan041768@gmail.com
init.defaultbranch=main
```

**2. GitHub 에서 저장소 생성 - 완료**

**3. 민감정보 보호**
```
yhmin@yhforwindows:~/workstation$ touch .gitignore
```































