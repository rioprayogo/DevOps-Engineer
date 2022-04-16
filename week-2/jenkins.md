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

* **download plugin yang dibutuhkan**
![logo](https://raw.githubusercontent.com/rioprayogo/DevOps-Engineer/main/week-2/assets/jenkins4.png)
![logo](https://raw.githubusercontent.com/rioprayogo/DevOps-Engineer/main/week-2/assets/jenkins5.png)

* **Buat akun untuk login kedalam jenkins**
![logo](https://raw.githubusercontent.com/rioprayogo/DevOps-Engineer/main/week-2/assets/jenkins6.png)

* **Buat kredensial untuk jenkins agar bisa terhubung ke server yang dituju**
![logo](https://raw.githubusercontent.com/rioprayogo/DevOps-Engineer/main/week-2/assets/jenkins7.png)

* **Tambahakan webhook agar jenkins dapat menerima perubahan pada repository github**
![logo](https://raw.githubusercontent.com/rioprayogo/DevOps-Engineer/main/week-2/assets/jenkins8.png)


* **Buat job baru untuk memulai pekerjaan**
![logo](https://raw.githubusercontent.com/rioprayogo/DevOps-Engineer/main/week-2/assets/jenkins9.png)

* **konfigurasikan job**

![logo](https://raw.githubusercontent.com/rioprayogo/DevOps-Engineer/main/week-2/assets/jenkins10.png)
![logo](https://raw.githubusercontent.com/rioprayogo/DevOps-Engineer/main/week-2/assets/jenkins11.png)

* **conotoh syntax pipeline Jenkinsfile**
```sh
def secret = 'app'
def server = 'app-rio@103.183.75.71'
def directory = 'wayshub-frontend'
def branch = 'main'

pipeline{
    agent any
    stages{
        stage ('docker delete & git pull'){
            steps{
                sshagent([secret]) {
                    sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
                    cd ${directory}
                    docker-compose down
                    docker system prune -f
                    git pull origin ${branch}
                    exit
                    EOF"""
                }
            }
        }
        stage ('docker compose'){
            steps{
                sshagent([secret]) {
                    sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
                    cd ${directory}
                    docker build -t rioprayogo/frontend:v.2 .
                    exit
                    EOF"""
                }
            }
        }
        stage ('docker up'){
            steps{
                sshagent([secret]) {
                    sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
                    cd ${directory}
                    docker-compose up -d
                    exit
                    EOF"""
                }
            }
        }
    }
}
```





