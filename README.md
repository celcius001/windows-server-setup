# **WINDOWS SERVER 2019 DOCKER SETUP**

## **INSTALL DOCKER ENGINE**

```ps
Install-Module DockerMsftProvider -Force -y

Install-Package -Name docker -ProviderName DockerMsftProvider -y

shutdown /r
```

## **INSTALL DOCKER-COMPOSE**

```ps
Invoke-WebRequest "http://github.com/docker/compose/release/download/1.26.2/docker-compose-Windows-x86_64.exe" -UseBasic -OutFile $Env:ProgramFiles\Docker\docker-compose.exe

```

---

## **INSTALL NODE IN DOCKER FOR windows/amd64**

```
docker pull stefanscherer/node-windows
```

---

## **RUN CONTAINER**

```
docker run -p $port:$port -d --restart unless-stopped $container_name $image_name
```

## **IF CONTAINER EXIST UPDATE**

```
 docker update --restart unless-stopped $container_name
```

---

## **INSTALL PORTAINER in Windows Server 2019**

```
docker create volume portainer
```

```yml
version: "3"
services:
  app:
    image: "portainer/portainer-ce:latest"
    ports:
      - "9000:9000"
    restart: "always"
    volumes:
      - '\\.\pipe\docker_engine\:\\.\pipe\docker_engine\'
      - 'portainer:C:\data\'
volumes:
  portainer:
    external: true
```
