---
title: DockerZN
date: {{ thu 30 2021 }}
tags:
- template
---

# Docker 

### Agenda
- Pengenalan Container
- Pengenalan Docker 
- Mengintall Docker 
- Arsitecture Docker
- Docker Image
- Docker Registry
- Docker Container 
- Docker Volume 
- Docker Network
- DLL

### Virtual Machine 

- Dalam dunia infrastructure, kita sudah terbiasa dengan yg namanya VM (Virtual Machine)
- Saat membuat sebuh VM, Biasanya kita akan menginstall system Operasi juga di VM
- Masalah yg terjadi ketika kita install VM adalah proses yg lambat ketika pe,buatan VM dan waktu yg di butuhkan untuk VM tersebut booting

#### Diagaram Virtual MAchine 

![Diagram VM ](image%20markdown/Diagram%20VM%20.png)

### Container

- Berbeda dengan VM, Container sendiri berfokus pada sisi Aplikasi
- Container sendiri sebernarnya berjalan di atas aplikasi Container Manager yg berjalan di sistem Operasi 
- Yang membedakan dengan VM adalah, Pada Container, kita bisa mem-package aplikasi dependency nya tanpa harus **menggabungkan sistem operasi**
- Container akan menggunakan  sistem operasi host dimana Container Manager nya berjalan [share resource host].
- Ukuran container biasanya hanya hitungan MB, berbeda dengan VM yg bisa sampai GB 
 
#### Diagaram Container 

![Diagram Container](image%20markdown/Diagram%20Container.png)


### Docker
#### Pengenalan Docker. 

- Docker adalah salah satu implentasi Container Manager yg saat ini paling populer 
- Docker merupakan teknologi yang masih baru,dikenalkan disekitar thun 2013
- Docker adalah aplikasi yang **free dan Open Source**
- https://www.Docker.com/

#### Docker Architecture

- Docker menggunakan **arsitecture Client-Server**
- Docker client berkomunikasi dengan Docker daemon (server)
- Saat kita menginstall Docker, Biasa nya didalamnya sudah terdapat Docker Client dan Docker Daemon
- Docker Client dan Docker Daemon bisa berjalan di satu sistem yang sama 
- Docker Client dan Docker Daemon berkomunikasi menggunakan **REST API**

![Diagram Docker Architecture ](image%20markdown/Diagram%20Docker%20Architecture%20.png)


#### Menginstall Docker 

- Docker bisa di install hampir disemua sistem operasi
- Untuk menginstall docker di Win dan MAc kita bisa menggunkan Docker Desktop
- https://docs.docker.com/get-docker/
- Untuk Linux, kita bisa install dari repository sesuai distro linux masing-masing
- https://docs.docker.com/enginer/install

#### Mengecek Docker 
- Untuk mengecek apakah Docker Daemon sudah berjalan, kita bisa gunakan :

  ` docker version `

#### Docker Registry

- Docker Registry adalah tempat kita Menyimpan Docker image
- Dengan menggunkan Docker Registry kita bisa menyimpan image yang kita but dan bisa digunakan di Docker Daemon dimanapun selama bisa terkoneksi dengan Docker Registry 
![Docker Registry v2](image%20markdown/Docker%20Registry%20v2.png)

#### Contoh Docker Registry 

- Docker Hub : https://hub.docker.com/
- Digital Ocean Container Registry : https://www.digitalocean.com/products/container-registry/
- Google Cloaud Container Registry : https://cloud.google.com/container-registry
- Amazon Elastic Container Registry: https://aws.amazon.com/ecr
- Azure Container Registry: https:/azure.microsoft.com/es-us/services/container-registry/
- 
#### Docker Image

- Docker image mirip seperti installer aplikasi, dimana didalam Docker image terdapat aplikasi dan dependency 
- Sebelum kita menjalankan applikasi di Docker, kita perlu memastikan memiliki Docker Image aplikasi tersebut

#### Melihat Docker image

- Untuk melihat Docker Image yang terdapat di dalam Docker Daemon, kita bisa menggunakan perintah:

  ` docker image ls`

#### Download Docker image

- untuk download Docker Image dari Docker Registry, kita bisa gunakan perintah : `docker image pull namaimage:tag`
- Kita bisa menjaci Docker Image yang ingin kita dowbload di https:/hub.docker.com/

#### Menghapus Docker Image

- jika kita tidak ingin menggunkan Docker image yang sudah kita download bisa menggunkan perintash berikut : 

  ` docker image rm alpine `

#### Docker Container 

-  Jika Docker images seperti installer aplikasi, maka Docker Container mirip seperti hasil installannya.
-  Satu Docker Image bisa digunankan untuk membuat beberap Docker Container, asalkan nama Docker Container nya berbeda.
-  Jika Kita sudah membuat Docker Container, Maka doker Image yang digunakan tidak bisa di hapus, hal ini dikarenakan sebeneranya **Docker Container tidak meng-copy isi Docker Images, tapi hanya menggunakan isi nya saja.**

##### Status Container 

- Saat kita membuat container, **secara default container tersebut tidak akan berjalan**
- Mirip seperti ketika kita mengistall aplikasi jika tidak kita jalankan, maka aplikasi tersebut tidak akan berjalan
- Oleh karena itu, setelah membuat container, kita perlu menjalankannya.

##### Melihat Container

- Untuk melihat Container, baik yang sedang berjalan atau tidak di Docker Daemon, kita bisa menggunakan command 

  `$ docker container ls - a`

- Sedangkan jika kita ingin melihat container yang sedah berjalan saja kita bisa gunakan command

  `$ docker container ls`
  
![Docker container logs v2](image%20markdown/Docker%20container%20logs%20v2.png)

##### Membuat Container 

- Untuk Membuat Container, Kita bisa gunakan perintah:

  ` $ docker container create --name namacontainer namaimage:tag`

ex :
  ` $ docker container create --name ContohRedis redis:lates`

   

##### Menjalankan Container 

- Untuk menjalankan container yang sudah kita buat, kita bisa menggunakan perintah sbb: 

  ` $ docker container start containerID/namaContainer ` 

 
##### Menghentikan Container 

- Untuk menghentikan Container, kita bisa menggunakan perintah sbb:
  
  `$ docker container stop containerID/namacontainer`
  

 ##### Menghapus Container 
 
 - Untuk menghapus container, tentunya dengan syarat kondisi docker sudah dalam keadaan distop, bisa menggunakan perintah sbb:
   
   `$ docker container rm containerID/namacontainer`

 
##### Container Log

- Kadang saat terjadi masalah dengan aplikasi yang terdapat di container, sering kali kita ingin melihat detail dari log aplikasi nya 
- Hal ini dilakukan untuk melihat detil kejadian apa yang terjadi di aplikasi, sehingga akan memudah kan kita ketika mendapat masalah

###### Melihat Container Log

- Untuk melihat log aplikasi di container kita, kita bisa menggunakan perintah: 
  `$ docker container logs containerID/namacontainer`
  
- Atau jika ingin melihat log secara realtime, kita juga bisa menggunakan perintah:
  `$ docker container logs -f containerID/namacontainer`
![Docker container logs](image%20markdown/Docker%20container%20logs.png)


##### Container Exec

- Saat kita membuat container, aplikasi yang terdapat di dalam container  hanya bisa di akses dari dalam container.
- Oleh karena itu, kadang kita perlu masuk ke dalam containernya itu sendiri
- Untuk masuk ke dalam container, kita bisa menggunakan fitur container exec, dimana digunakan untuk mengeksekusi kode program yang terdapat di dalam container.

##### Masuk ke Container 

- Untuk masuk ke dalam continer, kita bisa mencoba mengeksekusi program bash script yang terdapat di dalam container dengan bantuan **container Exec**
  `$ docker container exec -i -t containerID/namacontainer /bin/bash`

- `-i` adalah argiment interaktif, menjaga input tetap aktif 
- `-t` adalah argument untuk alokasi **pseudo-TTY** (terminal akses)
- `/bin/bash` contoh kode program yang terdapat di dalam container 


##### Container Port 

- Saat menjalankan container, container tersebut terisolasi di dalam Docker
- Artinya sistem host, tidak dapat mengakses aplikasi yang ada di dalam container secara langsung, salah satu cara nya adalah menggunakan **Container Exec** untuk masuk kedalam container.
- Biasanya, Sebuah aplikasi berjalan pada **port** tertentu   

###### Port Forwarding

- Docker memiliki kemampuan untuk melakukan **port forwading**, yaitu meneruskan sebuah port yang terdapat di sistem hostnya kedalam Docker Container 
- Cara ini cocok jika kita ingin mengekspos port yang terdapat di container ke luar melalui sistem hostnya 

###### Melakukan Port forwarding

- Untuk melakukan port forwarding, kita bisa menggunkan perintah berikut ketika membuat container nya

`$ docker container create --name namacontaincer --publish porthost:portcontainer image:tag`

- Jika kita ingin melakukan port forwarding lebih dari satu, kita bisa tambahkan dua kali parameter `--publish` 

- Publish juga bisa di singkat memggunakan 
`$ docker container create --name contohnginx --publish 8080:80

![docker nginx](image%20markdown/docker%20nginx.png) 
![Nginx](image%20markdown/Nginx.png)

================================================================================

##### Container Enviroment Variable 

- Saat Membuat Aplikasi Menggunakan **Environment Variable** adalah salah satu teknik agar konfigurasi aplikasi bisa diubah secara dinamis.

- Dengan menggunakan enviorment variable, kita bisa mengubah2 konfigurasi aplikasi, tanpa harus mengubah code aplikasi nya.

- Docker Container memiliki parameter yang bisa kita gunakan untuk mengirim environment variable ke aplikasi yang terdapat di container.


##### Menambah Environment Variable

- Untuk menambah environment variable, kita bisa menggunakan perintah `--env` atau `e` misal: 

`docker container create --name namaconatiner --env KEY="value" --env KEY2="value" image:tag`

![docker env](image%20markdown/docker%20env.png)



##### Container Stats

- Saat menjalankan beberapa container di sistem host, penggunaan resource seperti CPU dan Memory hanya terlihat digunakan oleh Docker saja
- Kadang kita ingin melihat detail dari penggunaan resource untuk tiap containernya 
- Untungnya docker memiliki kemampuan untuk melihat penggunnaan resource dari setiap container yang sedang berjalan 
- Kita bisa gunakan command sbb:
` $ docker container stats`


##### Container Resource Limit

- Saat membuat container, secara default dia akan menggunkan semua CPU dan Memory yang diberikan ke Docker (Mac dan Windows) dan akan menggunakan semua CPU dan Memory yang tersedia di sistem Host(linux)
- Jika terjadi kesalahan, misal container terlalu banyak memakan CPU dan Memory, maka akan berdampak terhadap performa container lain, atau bahkan ke sistem host
- Oleh kerena itu ada baiknya ketika kita membuat container, kita membarika resource limit terhadap container nya.

###### Memory
- Saat Membuat Container, kita akan bisa menentukan jumlah memory yang bisa digunakan oleh container ini, dengan menggunakan perintah `--memory` diikuti dengan angka memory yang di perbolehkan untuk digunakan
- kita bisa menambahkan ukuran dalam bentuk **b(bytes), k(kilo bytes) m (mega byte) atau g (giga bytes)**

ex: 100m artinya 100 mega bytes

###### CPU
- Selain mengatur Memory, Kita juga bisa menentukan berapa jumlah CPU yang bisa digunkan oleh container dengan parameter `--cpu`
- Jika misal kita set dengan nilai 1.5 artinya container bisa menggunakan satu dan setengah CPU CORE

![docker resource limit ](image%20markdown/docker%20resource%20limit%20.png)


#### Bind Mounts

- Bind Mounts merupakan kemampuan melakukan mounting (sharing) file atau folder yang terdapat di sistem host ke container yang terdapat di docker
- Fitur ini sangat berguna ketika misal kita ingin mengirim konfigurasi dari luar container, atau misal menyimpan data yang dibuat di aplikasi di dalam container ke dalam folder di sistem host 
- Jika File ato folder tidak ada di sistem host, Secara otomatis akan dibuatkan oleh docker
- Untuk melakukan mounting, kita bisa menggunakan parameter`--mount` ketika membuat container 
- isi dari parameter `--mount` memiliki aturan tersendiri 

 ![docker mount](image%20markdown/docker%20mount.png)
 
 ##### Melakukan Mounting
 
 - Untuk melakukan Mounting, kita bisa menggunakan perintah berikut :

`$ docker container create --name namacontainer --mount "tyoe=bind,source=folder,destination=folder,readonly" image:tag`

ex: 

`$ docker container create --name mongodata --mount "type=bind,source=/Users/uchan/mongo-data,destination=/data/db" --publish 27017:27017 -env MONGO_INITDB_ROOT_USERNAME=uchan --env MONGO_INITDB_ROOT_PASSWORD=UCHAN mongo:latest`

`docker container create --name mongodata --publish 27018:27018 --mount "type=bind,source=/Users/RU9946/Documents/Ruslan/Docker/my-Docker/mongodb,destination=/data/db" --env MONGO_INITDB_ROOT_USERNAME=uchan --env MONGO_INITDB_ROOT_PASSWORD=uchan mongo:latest`

![docker mount data ](image%20markdown/docker%20mount%20data%20.png)

#### Docker Volume

- Fitur Bind Mounts sudah ada sejak Docker versi awal, diversi terbaru direkomendasikan menggunakan Docker Volume
- Docker Volume mirip dengan Bind Mounts, bedanya adalah terdapat management Volume, dimana kita bisa membuat volume, melihat daftar volume dan menghapus volume
- Volume sendiri bisa dianggap storage yang digunakan untuk menyimpan data, bedanya dengan Bind Mounts, data disimpan pada sistem host, sedangkan pada volume, data dimanage di docker

##### Melihat Docker Volume

- Saat kita membuat container, dimanakah data di dalam container itu disimpan, secara default semua data container disimpan di dalam volume 
- Jika kita coba melihat docker volume, kita akan lihat bahwa ada banyak volume yang sudah terbuat, walaupun kita belum pernah membuatnya sama sekali
- Kita bisa menggunakan command berikut untuk melihat daftar volume :
`docker volume ls` 

![docker volume](image%20markdown/docker%20volume.png)

##### Membuat Volume 
