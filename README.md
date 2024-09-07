## 👋 Welcome to webmin 🚀  

webmin README  
  
  
## Install my system scripts  

```shell
 sudo bash -c "$(curl -q -LSsf "https://github.com/systemmgr/installer/raw/main/install.sh")"
 sudo systemmgr --config && sudo systemmgr install scripts  
```
  
## Automatic install/update  
  
```shell
dockermgr update webmin
```
  
## Install and run container
  
```shell
mkdir -p "$HOME/.local/share/srv/docker/webmin/rootfs"
git clone "https://github.com/dockermgr/webmin" "$HOME/.local/share/CasjaysDev/dockermgr/webmin"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/webmin/rootfs/." "$HOME/.local/share/srv/docker/webmin/rootfs/"
docker run -d \
--restart always \
--privileged \
--name casjaysdevdocker-webmin \
--hostname webmin \
-e TZ=${TIMEZONE:-America/New_York} \
-v "$HOME/.local/share/srv/docker/casjaysdevdocker-webmin/rootfs/data:/data:z" \
-v "$HOME/.local/share/srv/docker/casjaysdevdocker-webmin/rootfs/config:/config:z" \
-p 80:80 \
casjaysdevdocker/webmin:latest
```
  
## via docker-compose  
  
```yaml
version: "2"
services:
  ProjectName:
    image: casjaysdevdocker/webmin
    container_name: casjaysdevdocker-webmin
    environment:
      - TZ=America/New_York
      - HOSTNAME=webmin
    volumes:
      - "$HOME/.local/share/srv/docker/casjaysdevdocker-webmin/rootfs/data:/data:z"
      - "$HOME/.local/share/srv/docker/casjaysdevdocker-webmin/rootfs/config:/config:z"
    ports:
      - 80:80
    restart: always
```
  
## Get source files  
  
```shell
dockermgr download src casjaysdevdocker/webmin
```
  
OR
  
```shell
git clone "https://github.com/casjaysdevdocker/webmin" "$HOME/Projects/github/casjaysdevdocker/webmin"
```
  
## Build container  
  
```shell
cd "$HOME/Projects/github/casjaysdevdocker/webmin"
buildx 
```
  
## Authors  
  
🤖 casjay: [Github](https://github.com/casjay) 🤖  
⛵ casjaysdevdocker: [Github](https://github.com/casjaysdevdocker) [Docker](https://hub.docker.com/u/casjaysdevdocker) ⛵  
