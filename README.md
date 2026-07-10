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
dockerHome="/srv/$USER/docker/casjaysdevdocker/webmin/webmin/latest/rootfs"
mkdir -p "/srv/$USER/docker/webmin/rootfs"
git clone "https://github.com/dockermgr/webmin" "$HOME/.local/share/CasjaysDev/dockermgr/webmin"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/webmin/rootfs/." "$dockerHome/"
docker run -d \
--restart always \
--privileged \
--name casjaysdevdocker-webmin-latest \
--hostname webmin \
-e TZ=${TIMEZONE:-America/New_York} \
-v "$dockerHome/data:/data:z" \
-v "$dockerHome/config:/config:z" \
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
      - "/srv/$USER/docker/casjaysdevdocker/webmin/webmin/latest/rootfs/data:/data:z"
      - "/srv/$USER/docker/casjaysdevdocker/webmin/webmin/latest/rootfs/config:/config:z"
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
