![header](https://capsule-render.vercel.app/api?type=slice&color=auto&height=100&section=header&text=Docker&fontSize=50&reversal=true&fontAlign=15)

# Docker

## Docker Document

- Docker Document: [Link][dockerdoclink]

[dockerdoclink]: https://docs.docker.com/get-docker "Docker Document"

- Install Docker Engine on Ubuntu: [Link][dockerinstalllink]

[dockerinstalllink]: https://docs.docker.com/engine/install/ubuntu/ "Go Install Docker Engine on Ubuntu"

### 1. Uninstall old version

```bash
sudo apt-get remove docker docker-engine docker.io containerd runc
```

### 2. Set up the repository

1. Update Apt Package

```bash
sudo apt-get update

sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

2. Docker Package 를 위한 Key 추가

```bash
sudo mkdir -m 0755 -p /etc/apt/keyrings

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

3. Set up the repository

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### 3. Install Docker Engine

1. Update the apt package

```bash
sudo apt-get update
```

<details>
<summary>GPG Error 발생 시</summary>

```bash
sudo chmod a+r /etc/apt/keyrings/docker.gpg
sudo apt-get update
```

</details>
<br>

2. Install Docker Engine, Containerd, Docker Compose.

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

3. 확인

```bash
sudo docker run hello-world
```

### 4. docker network 설치(NPM 전용)

```bash
sudo docker network create nginx-proxy-manager
```

> NPM 에서 Proxy Host 등록할 컨테이너들을 동일한 network 로 지정하기 위함.
>
> > NPM 에서 도커 컨테이너 서비스들을 Proxy Host 등록하는데
> > NPM 과 각 도커 컨테이너들을 동일한 docker network로 지정해주면
> > 불필요한 컨테이너 실행시 포트 포워딩과 포트 오픈을 하지 않아도 됨.
