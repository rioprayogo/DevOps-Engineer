# DevOps Engineer
## Week 1
### Setup database

* Install database mysql-server dengan menjalankan
```sh
sudo apt install mysql-server
```
- jalankan `sudo systemctl status mysql.service` untuk mengetahui status dari service mysql
 ![logo](https://raw.githubusercontent.com/DevOps-Engineer/main/week-1/asset/db1.png)

 * Langkah selanjutnya setelah melakukan install mysql pastikan menjalankan `sudo mysql_secure_installation` untuk mengamankan database
 ```sh
sudo mysql_secure_installation
```
 ![logo](https://raw.githubusercontent.com/DevOps-Engineer/main/week-1/asset/db2.png)
 ![logo](https://raw.githubusercontent.com/DevOps-Engineer/main/week-1/asset/db3.png)

 # Command dalam mysql
 * **untuk masuk ke database**
 ```sh
 sudo mysql -u root -p
 ```
 * **untuk membuat user**
  ```sh
CREATE USER 'new_user'@'%' IDENTIFIED BY 'password';
```
  ```sh
GRANT ALL PRIVILEGES ON *.* TO 'new_user'@'%';
```
```sh
FLUSH PRIVILEGES;
```
* **untuk membuat database**
```sh
CREATE DATABASE nama_database;
```
* **untuk melihat database**
```sh
SHOW DATABASES;
```
* **untuk melihat table database**
```sh
SHOW TABLES;
```
 ![logo](https://raw.githubusercontent.com/DevOps-Engineer/main/week-1/asset/db3.png)
 ![logo](https://raw.githubusercontent.com/DevOps-Engineer/main/week-1/asset/db4.png)

 * Lakukan config pada database mysql ubuh bind-address menjadi `0.0.0.0` pada file
 ```sh
 sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
 ```
  ![logo](https://raw.githubusercontent.com/DevOps-Engineer/main/week-1/asset/db5.png)


 * Hasil tables setelah di migrasi dari backend
  ![logo](https://raw.githubusercontent.com/DevOps-Engineer/main/week-1/asset/db6.png)


