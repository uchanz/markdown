# Basic HTTP

## Pengenalan HTTP

- HTTP singkatan dari *Hypertext Transfer Protocol*.
- HTTP Merupakan protokol untuk melakukan transmisi hypermedia document, seperti *HTML, JavaScript, CSS, Image, Audio dan lain2*.
- HTTP awalnya didesign untuk komunikasi antara *Web Browser*, Namun saat ini juga digunakan untuk keperluan lain.

### Client Server 

- HTTP mengikuti arsitekture *client dan Server*.
- Client mengirimkan HTTP request untuk meminta atau mengirim informasi ke Server.
- Kemudian Server membalasnya dengan *HTTP Response* dari *HTTP Request* yang di terima.

[![Client-Server.jpg](https://i.postimg.cc/0NBD1NNk/Client-Server.jpg)](https://postimg.cc/R3wNc4fy)

### Plain Language and Human Readable

HTTP didesain menggunkan bahasa yang mudah dimengerti oleh bahasa manusia, seperti:

- GET
- POST
- PUT
- DELETE
- HEAD
- OPTION


### Stateless

- HTTP merupakan protokol yang **StateLess**.
- Artinya tiap HTTP Request merupakan request yang indenpenden, tidak ada keterkaitan atau hubungan dengan HTTP Request Sebelum atau Sesudah nya.
- Hal ini dilakukan agar HTTP Request tidak harus dilakukan dalam *sequences*, Sehingga client bisa melakukan HTTP Request secara bebas tanpa adanya aturan harus dimulai dari mana. 

### Session

- Jika HTTP Merupakan protokol yang *stateless*, Bagaimana dengan dengan Session? misal Client harus login terlebih dahulu sebelum berinteraksi?
- Untuk menangani permasalahan seperti ini, HTTP memiliki fitur yang bernama **HTTP Cookies**.
- HTTP Cookie memaksa client menyimpan informasi yang diberikan server.

## HTTP Version

- Spesifikasi HTTP selalu di perbarui.
- Saat ini, Kebanyakan Web berjalan di HTTP/1.1 atau HTTP2
- HTTP2 mulai hadir sekitar tahun 2015 dan saat ini sudah banyak diadopsi oleh semua Web di Dunia

### HTTP/1.1 vs HTTP/1.2

- Saat ini HTTP/1.1 merupakan fallback protocol, dimana Web Browser secara default akan melakukan request menggunakan HTTP/1.2. Jika Web browser tidak mendukung, maka web browser akan melakukan fallback ke protocol HTTP/1.1
- Secara garis besar specifikasi HTTP/2 sama dengan HTTP/1.1, yang membedakan adalah pada HTTP/2, HTTP request yang dikirim dalam bentuk text, secara otomatis akan menjadi *binary* sehingga lebih cepat daripada HTTP/1.1
- Selain itu HTTP/2 , menggunakan algoritma kompresi untuk memperkecil request dan mendukung multiplexing, sehingga bisa mengirin beberapa request dalam satu connection yang sama.
- Dari sisi pembuatan, tidak ada perbedaaan, semua ini biasanya sudah diurus secara otomatis oleh Web Server yang kita gunakan.

### HTTPS
- Secara default, HTTP tidaklah aman.
- HTTPS merupakan HTTP dengan Enkripsi.
- Perbedaan HTTP dengan HTTPS adalah, HTTP menggunkan SSL (Secure Socket layer) untuk melakukan enkripsi HTTP Request dan HTTP Response
- Hasil nya HTTPS jauh lebih aman dibanding dengan HTTP biasa.
- Web yang menggunkan HTTP akan menggunakan `https://` pada url nya, dan yang hanya bisa HTTP akan menggunakan `http://`
- 

## HTTP Terminology

- Saat kita belajar HTTP, ada banyak sekali menggunkan terminologi, istilah atau teknologi.
- Dan kita perlu mengerti tentang hal tersebut.

### Web Browser

- Merupakan aplikasi yang digunakan untuk mengakses Web menggunkan protokol HTTP
- Contohnya : Google chrome, Mozila, Edge, dan safari.

### TCP 

- TCP (Transmission Transfer Protocol) adalah satu protokol jaringan komputer yang biasa digunakan oleh Web,FTP dll.
- Jika kita menggunkan jaringan internet,  Kemungkinan besar kita akan menggunakan protocol TCP untuk melakukan koneksi jaringan nya.

### IP

- IP (Internet Protocol).
- IP digunakan sebagai identitas komputer di jaringan.
- Setiap komputer baik itu client dan server akan memiliki IP.

### URL

- URL (Uniform Resource Locator).
- URL merupakan sauatu alamat dari sebuah Web.

### DNS

- DNS (Domain Name Server).
- DNS merupakan tempat yang berisi dara dari pemetaan antara nama domain di URL menuju lokasi IP komputer 
- Saat Web Browser mengakses sebuah domain di web. sebenernya proses nya akan bertanya ke DNS untuk mendapatkan IP terlebih dahulu dari web yang dituju

### Web Server

- Web Server merupakan aplikasi yang berjalan di jaringan internet yang bertugas sebagi server.
- Web server berisi informasi dan datan yang bisa di akses oleh client 
- Web Server akan menerima request dalie client, dan membalas request tersebut berupa informasi yang diminta oleh client.

## HTTP Flow

- Bagaimana alur kerja si HTTP
- Dalam HTTP, biasanya terdapat dua pihak yang terlibat, yaitu Client dan Server.
- Client akan mengirimkan request.
- dan Server akan menerima Request dan membalas dengan response.

### Server 

- Server merupakan sebuah komputer, dimana semua informasi disimpan pada komputer tersebut.
- Komputer server biasanya menjalankan service Web Server agar bisa menerima protocol HTTP.

### Client

- Client merupakan komputer yang bertugas mengirmkan HTTP Request ke komputer Server.
- Untuk mengirim request HTTP, Bisanya Client akan menggunkan applikasi Web Browser.
- Server dan Client harus dapat terkoneksi agar dapat berkomunikasi

### Request

- Client akan mengirimkan request ke server dalam bentuk HTTP Request
- HTTP request berisikan informasi seperti lokasi resource, data yang dikirim jika ada, dan lain lain.
- HTTP Request akan diterima oleh Server
- Selanjutnya Server akan memproses request yang diminta oleh Client tersebut.

### Response

- Setelah Server memproses HTTP Request yang dikirm oleh Client.
- Server akan membalas dengan HTTP Response.
- HTTP Response biasa nya akan berisikan data yang diminta oleh client dalam HTTP Request.

[![request-and-response.jpg](https://i.postimg.cc/gj1mLWLd/request-and-response.jpg)](https://postimg.cc/hQ8HNN03)

## Browser Network Tool

- Untuk mempermudah melihgat apa yang dilakukan di belakang Web browser, biasanya Web browser memiliki fitur **Network tool**.
- Contohnya di  browser google chrome dan Firefox sudah memilikit network tool
- Dengan Network tool, kita bisa melihat dengan detil HTTP Request dan HTTP Response yang dilakukan oleh Client dan server.