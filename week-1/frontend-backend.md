# DevOps Engineer
## Week 1
### Deploy Frontend & Backend

* Persiapkan aplikasi frontend dan backend
**frontend**
```sh
git clone https://github.com/rioprayogo/wayshub-frontend.git
```
**backend**
```sh
git clone https://github.com/rioprayogo/wayshub-backend.git
```
![logo](https://raw.githubusercontent.com/rioprayogo/DevOps-Engineer/main/week-1/assets/app1.png)


* Persiapkan engine untuk menjalankan aplikasi
**nvm**
```sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```
 ![logo](https://raw.githubusercontent.com/DevOps-Engineer/blob/main/week-1/asset/app2.png)

* Jika sudah lakukan npm install pada frontend dan backend untuk membuat node module
 ![logo](https://raw.githubusercontent.com/DevOps-Engineer/blob/main/week-1/asset/app3.png)
 ![logo](https://raw.githubusercontent.com/DevOps-Engineer/blob/main/week-1/asset/app4.png)

 * Lakukan config `sudo nano /frontend/src/config/api.js` pada frontend agar dapat terhubung dengan backend
  ![logo](https://raw.githubusercontent.com/DevOps-Engineer/blob/main/week-1/asset/app5.png)

* Lakukan config `sudo nano /backend/config/config.json` pada backend agar dapat tehubung dengan database
  ![logo](https://raw.githubusercontent.com/DevOps-Engineer/blob/main/week-1/asset/app7.png)

* Install sequleize yang berfungsi memetakan data untuk migrasi ke database
**install sequelize**
```sh
npm install sequelize-cli -g
```
**untuk menjalankan sequelize**
```sh
npx sequelize db:migrate
```
![logo](https://raw.githubusercontent.com/DevOps-Engineer/blob/main/
week-1/asset/app8.png)
![logo](https://raw.githubusercontent.com/DevOps-Engineer/blob/main/week-1/asset/app9.png)

* Gunakan pm2 agar aplikasi dapat berjalan di background
**untuk mendownload pm2**
```sh
npm install pm2
```
* Jalankan dan configurasikan pm2 dengan `pm2 ecosystem simple` dan `pm2 start` untuk mendapatkan file ecosystem.config.js dan menjalankanya

![logo](https://raw.githubusercontent.com/DevOps-Engineer/blob/main/week-1/asset/app11.png)
![logo](https://raw.githubusercontent.com/DevOps-Engineer/blob/main/week-1/asset/app12.png)
![logo](https://raw.githubusercontent.com/DevOps-Engineer/blob/main/week-1/asset/app13.png)
