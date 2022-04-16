# DevOps Engineer
## Week 2
### Jenkins

* **install jenkins**
`Perbarui OS`
```sh
sudo apt update
```
`Instal OpenJDK`
```sh
sudo apt install openjdk-11-jdk
```
`Impor Kunci GPG`
```sh
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key tambahkan -
```
`tambah repo jenkins`
```sh
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
```
`Perbarui OS`
```sh
sudo apt update
```
`Instal Jenkins`
```sh
sudo apt install jenkins
```
* **file password defult** `/var/lib/jenkins/secrets/initialAdminPassword`
* **port defult jenkins 8080**

![logo](https://raw.githubusercontent.com/rioprayogo/DevOps-Engineer/main/week-2/assets/jenkins2.png)
![logo](https://raw.githubusercontent.com/rioprayogo/DevOps-Engineer/main/week-2/assets/jenkins3.png)

