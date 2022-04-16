# DevOps Engineer
## Week 2
### Docker

* `**install docker & docker compose**`
`Update your existing packages:`
```sh
sudo apt update
```
`Install a prerequisite packages which let apt utilize HTTPS:`
```sh
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
`Add GPG key for the official Docker repo to the Ubuntu system:`
```sh
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
`Add the Docker repo to APT sources:`
```sh
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
```
`Update the  database with the Docker packages from the added repo:`
```sh
sudo apt update
```
`Install Docker software:`
```sh
sudo apt install docker-ce
```

`**untuk docker compose**`
```sh
sudo curl -L "https://github.com/docker/compose/releases/download/1.28.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
```sh
sudo chmod +x /usr/local/bin/docker-compose
```

* **agar docker tidak menggunakan sudo**
```sh
sudo usermod -aG docker ${USER}
```

* **beberapa perintah dalam docker**
`docker run --name (namacontainer) -p (port) -e (environment) -v (volume) (image)`
`docker build -t (name):(tagname)`
`docker compose up -d`


* Persiapkan aplikasi frontend dan backend
**frontend**
```sh
git clone https://github.com/rioprayogo/wayshub-frontend.git
```
**backend**
```sh
git clone https://github.com/rioprayogo/wayshub-backend.git
```
* Lakukan config `sudo nano /frontend/src/config/api.js` pada frontend agar dapat terhubung dengan backend

* Lakukan config `sudo nano /backend/config/config.json` pada backend agar dapat tehubung dengan database

* Buat folder dengan nama `Dockerfile` yang berfungsi untuk membuat aplikasi menjadi images docker
```sh
FROM node:10
WORKDIR /usr/src/app
COPY . .
RUN npm install
EXPOSE 3000
CMD ["npm", "run", "start;"]
```
* Jalankan `docker build -t [name]:[tagname] .` untuk menjalankan dockerfile mengubah aplikasi menjadi image
**contoh**
```sh
docker build -t rioprayogo:frontend:v.2 .
```
![logo](https://raw.githubusercontent.com/rioprayogo/DevOps-Engineer/main/week-2/assets/docker1.png)

* Jalankan docker push untuk menyimpan image di docker registry
```sh
docker push rioprayogo/frontend:v.2
```
![logo](https://raw.githubusercontent.com/rioprayogo/DevOps-Engineer/main/week-2/assets/docker3.png)

* **lakukan hal yang sama pada backend**
* isi Dockerfile dari backend
```sh
FROM node:10
WORKDIR /usr/src/app
COPY . .
RUN npm install
RUN npm install sequelize-cli -g
RUN npx sequelize db:migrate
EXPOSE 5000
CMD ["npm", "run", "start;"]
```
![logo](https://raw.githubusercontent.com/rioprayogo/DevOps-Engineer/main/week-2/assets/docker4.png)
![logo](https://raw.githubusercontent.com/rioprayogo/DevOps-Engineer/main/week-2/assets/docker6.png)

* docker compose digunakan untuk menjalankan beberapa container sekaligus
**contoh isi file docker compose**
```sh
version: '3.7'
#networks:
#  rionet:
#    external: true

services:
  frontend:
    container_name : frontend
    image: rioprayogo/frontend:v.2
    stdin_open: true
    ports:
      - "3000:3000"

  backend:
    container_name : backend
    image: rioprayogo/backend:v.2
    ports:
      - "5000:5000"
```
* cara menjalankan docker compose dengan perintah
```sh
docker compose build -d
```


