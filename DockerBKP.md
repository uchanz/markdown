---
title: DockerZN
date: {{ thu 30 2021 }}
tags: Docker
- GENERAL TEMPLATE 
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

## Virtual Machine 

- Dalam dunia infrastructure, kita sudah terbiasa dengan yg namanya VM (Virtual Machine)
- Saat membuat sebuh VM, Biasanya kita akan menginstall system Operasi juga di VM
- Masalah yg terjadi ketika kita install VM adalah proses yg lambat ketika pe,buatan VM dan waktu yg di butuhkan untuk VM tersebut booting

#### Diagaram Virtual MAchine 

![Virtual Machine](image%20markdown/IMG_0193.jpg)

## Container

- Berbeda dengan VM, Container sendiri berfokus pada sisi Aplikasi
- Container sendiri sebernarnya berjalan di atas aplikasi Container Manager yg berjalan di sistem Operasi 
- Yang membedakan dengan VM adalah, Pada Container, kita bisa mem-package aplikasi dependency nya tanpa harus menggabungkan sistem operasi 
- Container akan menggunakan  sistem operasi host dimana Container Manager nya berjalan [share resource host].
- Ukuran container biasanya hanya hitungan MB, berbeda dengan VM yg bisa sampai GB 
 
#### Diagaram Container 

![Container](image%20markdown/IMG_0194.PNG)

## Docker
### Pengenalan Docker. 

- Docker adalah salah satu implentasi Container Manager yg saat ini paling populer 
- Docker merupakan teknologi yang masih baru,dikenalkan disekitar thun 2013
- Docker adalah aplikasi yang free dan Open Source
- https://www.Docker.com/

#### Docker Architecture
- Docker menggunakan arsitecture Client-Server
- Docker client berkomunikasi dengan Docker daemon (server)
- Saat kita menginstall Docker, Biasa nya didalamnya sudah terdapat Docker Client dan Docker Daemon
- Docker Client dan Docker Daemon bisa berjalan di satu sistem yang sama 
- Docker Client dan Docker Daemon berkomunikasi menggunakan REST API


![Docker Architecture ](image%20markdown/IMG_0195.jpg)

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
[image Docker Registry]

#### Contoh Docker Registry 

- Docker Hub : https://hub.docker.com/
- Digital Ocean Container Registry : https://www.digitalocean.com/products/container-registry/
- Google Cloaud Container Registry : https://cloud.google.com/container-registry
- Amazon Elastic Container Registry: https://aws.amazon.com/ecr
- Azure Container Registry: https:/azure.microsoft.com/es-us/services/container-registry/
- 
#### Docker Image
- Docker image mirip seperti installer aplikasi, dimana di dalam Docker image terdapat aplikasi dab dependency 
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
-  Jika Docker images seperti installer aplikasi, maka Docker Container mirip seperti hasil installannya 
-  Satu Docker Image bisa digunankan untuk membuat beberap Docker Container, asalkan nama Docker Container nya berbeda.
-  Jika Kita sudah membuat Docker Container, Maka doker Image yang digunakan tidak bisa di hapus, hal ini dikarenakan sebeneranya Docker Container tidak meng-copy isi Docker Images, tapi hanya menggunakan isi nya saja
-  