# Linux Facebook App

Esta una página muy sencilla montada sobre un servidor NGINX que permite a los usuarios compartir un post de facebook.

Requisito tener Git y Docker instalado y tener una cuenta en [Docker Hub](https://hub.docker.com/)
Si no tienes Git ni Docker instalados puedes utilizar [Docker for Beginners](https://training.play-with-docker.com/beginner-linux/)

Instrucciones:

### Clonar el repositorio

`git clone https://github.com/GaboGomez09/linux_fb_app`

### Entra al proyecto 

` cd ~/linux_fb_app`

### Despliega los contenidos del Dockerfile

`cat Dockerfile`

### Establece tu id de Dockerhub

`export DOCKERID=<tu docker id>`

### Asegúrate que esta asignada tu variable correctamente

`echo $DOCKERID`

### Construye la imagen a partir del Dockerfile

`docker image build --tag $DOCKERID/linux_fb_app:1.0 .`

### Corre un nuevo contenedor a partir de tu imagen

`docker container run --detach --publish 80:80 --name linux_fb_app $DOCKERID/linux_fb_app:1.0`

### Entra al siguiente link para ver tu app

`localhost:80`

### Borra tu contenedor

`docker container rm --force linux_fb_app`
 
### ¿Y cómo cambio mi proyecto mientras está dentro del contenedor?
 
 `docker container run --detach --publish 80:80 --name linux_fb_app --mount type=bind,source="$(pwd)",target=/usr/share/nginx/html $DOCKERID/linux_fb_app:1.0`

### Revisa que está bien desplegada tu página en:

`localhost:80`

### Cambiemos nuestra página por otra

 `cp index-new.html index.html`

### Revisa tu página para ver el cambio

`localhost:80`

### Si estás en tu compus personal no olvides eliminar el contenedor para no tener un proceso corriendo

 `docker container rm --force linux_fb_app`