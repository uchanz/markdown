---
title: DockerZN
date: {{ thu 30 2021 }}
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

[![Diagram-Virtual-Machine.png](https://i.postimg.cc/XNKXDn3V/Diagram-Virtual-Machine.png)](https://postimg.cc/0rQ8zRb3)


### Container

- Berbeda dengan VM, Container sendiri berfokus pada sisi Aplikasi
- Container sendiri sebernarnya berjalan di atas aplikasi Container Manager yg berjalan di sistem Operasi 
- Yang membedakan dengan VM adalah, Pada Container, kita bisa mem-package aplikasi dependency nya tanpa harus **menggabungkan sistem operasi**
- Container akan menggunakan  sistem operasi host dimana Container Manager nya berjalan [share resource host].
- Ukuran container biasanya hanya hitungan MB, berbeda dengan VM yg bisa sampai GB 
 
#### Diagaram Container 

[![Diagram-Container.png](https://i.postimg.cc/R0jq2FN0/Diagram-Container.png)](https://postimg.cc/nsGHDnK8)


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

[![Diagram-Docker-Architecture.png](https://i.postimg.cc/vTvB1tX1/Diagram-Docker-Architecture.png)](https://postimg.cc/4HmZqtDZ)


#### Menginstall Docker 

- Docker bisa di install hampir disemua sistem operasi
- Untuk menginstall docker di Win dan MAc kita bisa menggunkan Docker Desktop
- https://docs.docker.com/get-docker/
- Untuk Linux, kita bisa install dari repository sesuai distro linux masing-masing
- https://docs.docker.com/enginer/install

#### Mengecek Docker 
- Untuk mengecek apakah Docker Daemon sudah berjalan, kita bisa gunakan :

  ` docker version `

[![Docker-Version.png](https://i.postimg.cc/zfLVdWDM/Docker-Version.png)](https://postimg.cc/cKSxCvnM)

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
  
[![Docker-container-logs-v2.png](https://i.postimg.cc/25JBmGXr/Docker-container-logs-v2.png)](https://postimg.cc/yJmNymHb)

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
  
[![Docker-container-logs.png](https://i.postimg.cc/NGRrq18v/Docker-container-logs.png)](https://postimg.cc/0r2N7KHV)


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
`$ docker container create --name contohnginx --publish 8080:80`

[![Nginx.png](https://i.postimg.cc/zXSWWn3F/Nginx.png)](https://postimg.cc/dL3LcZ2h)

================================================================================

##### Container Enviroment Variable 

- Saat Membuat Aplikasi Menggunakan **Environment Variable** adalah salah satu teknik agar konfigurasi aplikasi bisa diubah secara dinamis.

- Dengan menggunakan enviorment variable, kita bisa mengubah2 konfigurasi aplikasi, tanpa harus mengubah code aplikasi nya.

- Docker Container memiliki parameter yang bisa kita gunakan untuk mengirim environment variable ke aplikasi yang terdapat di container.


##### Menambah Environment Variable

- Untuk menambah environment variable, kita bisa menggunakan perintah `--env` atau `e` misal: 

`docker container create --name namaconatiner --env KEY="value" --env KEY2="value" image:tag`

[![docker-env.png](https://i.postimg.cc/PqN8B9yS/docker-env.png)](https://postimg.cc/kV34SjkS)



##### Container Stats

- Saat menjalankan beberapa container di sistem host, penggunaan resource seperti CPU dan Memory hanya terlihat digunakan oleh Docker saja
- Kadang kita ingin melihat detail dari penggunaan resource untuk tiap containernya 
- Untungnya docker memiliki kemampuan untuk melihat penggunnaan resource dari setiap container yang sedang berjalan 
- Kita bisa gunakan command sbb:
` $ docker container stats`

[![docker-stats.png](https://i.postimg.cc/PJ1DSDyh/docker-stats.png)](https://postimg.cc/7JYb6fjQ)

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

[![docker-resource-limit.png](https://i.postimg.cc/13mFKfqh/docker-resource-limit.png)](https://postimg.cc/7fRbHP9m)


#### Bind Mounts

- Bind Mounts merupakan kemampuan melakukan mounting (sharing) file atau folder yang terdapat di sistem host ke container yang terdapat di docker
- Fitur ini sangat berguna ketika misal kita ingin mengirim konfigurasi dari luar container, atau misal menyimpan data yang dibuat di aplikasi di dalam container ke dalam folder di sistem host 
- Jika File ato folder tidak ada di sistem host, Secara otomatis akan dibuatkan oleh docker
- Untuk melakukan mounting, kita bisa menggunakan parameter`--mount` ketika membuat container 
- isi dari parameter `--mount` memiliki aturan tersendiri 

 [![docker-mount.png](https://i.postimg.cc/RVzKNPC0/docker-mount.png)](https://postimg.cc/V5DdhWCy)
 
 ##### Melakukan Mounting
 
 - Untuk melakukan Mounting, kita bisa menggunakan perintah berikut :

`$ docker container create --name namacontainer --mount "tyoe=bind,source=folder,destination=folder,readonly" image:tag`

ex: 

`$ docker container create --name mongodata --mount "type=bind,source=/Users/uchan/mongo-data,destination=/data/db" --publish 27017:27017 -env MONGO_INITDB_ROOT_USERNAME=uchan --env MONGO_INITDB_ROOT_PASSWORD=UCHAN mongo:latest`

`docker container create --name mongodata --publish 27018:27018 --mount "type=bind,source=/Users/RU9946/Documents/Ruslan/Docker/my-Docker/mongodb,destination=/data/db" --env MONGO_INITDB_ROOT_USERNAME=uchan --env MONGO_INITDB_ROOT_PASSWORD=uchan mongo:latest`

[![docker-mount-data.png](https://i.postimg.cc/QddBTw2j/docker-mount-data.png)](https://postimg.cc/D8RyVjfN)

#### Docker Volume

- Fitur Bind Mounts sudah ada sejak Docker versi awal, diversi terbaru direkomendasikan menggunakan Docker Volume
- Docker Volume mirip dengan Bind Mounts, bedanya adalah terdapat management Volume, dimana kita bisa membuat volume, melihat daftar volume dan menghapus volume
- Volume sendiri bisa dianggap storage yang digunakan untuk menyimpan data, bedanya dengan Bind Mounts, data disimpan pada sistem host, sedangkan pada volume, data dimanage di docker

##### Melihat Docker Volume

- Saat kita membuat container, dimanakah data di dalam container itu disimpan, secara default semua data container disimpan di dalam volume 
- Jika kita coba melihat docker volume, kita akan lihat bahwa ada banyak volume yang sudah terbuat, walaupun kita belum pernah membuatnya sama sekali
- Kita bisa menggunakan command berikut untuk melihat daftar volume :
`docker volume ls` 

[![docker-volume.png](https://i.postimg.cc/8zZ6XNRF/docker-volume.png)](https://postimg.cc/FYJz7tnm)

##### Membuat Volume 

- Untuk mebuat Volume , kita busa gunakan perintah :

`$ docker volume create namavolume'

##### Menghapus Volume

- Volume yang tidak digunakan oleh container bisa kita hapus, tapi jika volume digunakan container, maka tidak bisa kita hapus sampai container nya dihapus
- Untuk menghapus Volume, kita bisa menggunakan perintah 

`$ docker volume rm namavolume`

##### Container Volume

- Volume yang sudah kita buat, bisa kita gunakan di container 
- Keuntungan menggunakan Volume adalah, jika container kita hapus, data akan tetap aman di volume 
- Cara menggunakan volume di container sama dengan menggunakan bind mount, kita bisa menggunakan parameter `--mount`, namun dengan menggunakan **type volume dan source nama volume** 


##### Backup Volume

- Sayang, sampai saat ini ,tidak ada cara otomatis melakukan backup volume yang sudah kita buat 
- Namun kita nosa memanfaatkancontainer untuk melakukan backup data yang ada di dalam volume ke dalam archive zip atau tar.gz

###### Tahapan Melakukan Backup

- Matikan container yang menggunakan volume yang kita ingin kita backup
- Buat Container baru dengan dua mount, Volume yang kita ingin kita backup, dan bind mount folder dari sistem host
- Lakukan backup menggunakan container dengan cara mengarchive isi volume dan simpan di bind folder 
- isi file backup sekarang ada di folder sistem host
- Delete container yang kita gunakan untuk melakukan backup

##### Restore Volume

- Setelah melakukan backup volumek ke dalam file archive, kita bisa menyimpan file archive tersebut ke tempat yang lebih aman, misal cloud storage
- Sekarang kita akan mencoba melakukan restore data backup ke volume yang baru, untuk memastikan data yang kita backup tidak corrupt

###### Tahapan Melakukan Restore 

- Buat Volume baru untuk melakukan restore data backup
- Buat Container baru dengan dua mount, Volume baru untuk restore backup dan bind mount folde dari sistem host yang berisi file backup.
- Lakukan restore dengan menggunakan container dengan cara mengextrak isi backup file kedalam volume 
- isi file backup sekarang sudah di restore ke volume 
- Delete container yang kita gunakan untuk melakukan restore 
- Volume baru yang berisi data backup siap digunakan oleh container baru 

##### Docker Network

- Saat kita membuat container di docker, secara default container akan salaing terisolasi satu sama lainya, jadi jika kita mencoba memanggil antar container, bisa dipastikan bahwa kita tidak akan bisa melakukan nya 
- Docker memeliliki fitur network yang bisa digunakan untuk membuat jaringan di dalam docker
- Dengan menggunakan Network, kita bisa mengkoneksikan container dengan container lain dalam satu network yang sama
- Jika beberap container terdapat pada satu Network yang sama, maka secara otomatis container tersebut bisa saling berkomunikasi 
- 