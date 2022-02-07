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


## HTTP Request dan HTTP Respon

- HTTP Request dana HTTP Response adalah sebuah HTTP message.
- HTTP Message memiliki standarisasi format.
- Dengan demikian, jika kita ingin membuat client dan server sendiri, Sebenernya bisa kita lakukan, asal kita mengikuti standarisasi format HTTP Message.

### HTTP Message untuk Request

berikut adalah format baku dari **HTTP Request** :

```

POST /login HTTP/1.1                }-------> Start line
Host: example.com                   }---------> Header
Connection: keep-alive.             }---------> Header
accept: application/json.           }---------> Header
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) }---------> Header
Content-Type: application/json      }---------> Header
Content-Length: 51                  }---------> Header
                                    }---------> Space
{"Password": "rahasia", "username" : "uchan"}. }---------> Body

```

pada bagian Header merepresentasikan "key" : "value" nya 

} ---> Space sebagai pemisah antara header dan body 

Berikut adalah format baku untuk **HTTP Response** nya :

```
HTTP/1.1 200.                                           }---------> Start line
Set-Cookie:X-COMMERCE-SESSION=eyJ0eXAi0iJKV1QiLCJhbGci0iJIUzI1  }---------> Header
Content-Type: application/json                          }---------> Header
Transfer-Encoding: chunked                              }---------> Header
Date: Sun, 04 Jul 2021 12:17:55 GMT                     }---------> Header
Keep-Alive: timeout=60                                  }---------> Header
Connection: keep-alive                                  }---------> Header
                                                        }---------> Space
{"status":"0K" , "code": 200, "data": {"username": "khannedy", "name" : "uchan" } }---------> Body

```

### HTTP Method

- Dalam HTTP Request, hal pertama yang harus kita tentukan terlebih dahulu tentukan adalah **HTTP Method**.
- HTTP Method mirip seperti kategory request 
- Ada banyak jenis HTTP method yang dapat digunakan ketika membuat http request, dan kita bisa sesuaikan dengan kubutuhan yang kita inginkan.

#### Jenis2 HTTP Method

| HTTP Method | Keterangan                                                                                                                                                                                                                                 |
|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `GET`       | GET Method digunakan untuk melakukan request data. Request menggunkan GET hanya menerima data dan bukan untuk mengirim data.                                                                                                               |
| `HEAD`      | HEAD Method digunakan sama seperti GET, tapi tambah membutuhkan **response body**.                                                                                                                                                         |
| `POST`      | POST methiod digunakan untuk mengirimkan data **baru** keserver, biasa digunkan untuk mengirim data baru sehingga biasa nya memiliki requestbody.                                                                                          |
| `PUT`       | PUT Method biasanya digunakan untuk mengganti semua data yang terdapat di server dengand data baru yang dikirim di **request**                                                                                                             |
| `DELETE`    | DELETE Method digunakan untuk menghapus data.                                                                                                                                                                                              |
| `PATCH`     | PATCH Method digunakan untuk mengubah sebagian data                                                                                                                                                                                        |
| `OPTIOSN`   | OPTION Method digunakan untuk mendeskripsikan opsi komunikasi yang tersedia.                                                                                                                                                               |
| `TRACE`     | TRACE Method merupakan request method untuk debugging. Response TRACE method akan mengemabalikan seluru informasi yang dikirim oleh client. Saat mebuat web sangat direkomendasikan untuk tidak TRACE method ketika sudah live prodduction |



## URL (Uniform Resource Locator)

- URL merupakan alamat dari senuah resource di Web
- URL wajib kita gunakan untuk menuju informasi Resource yang akan kita tuju dalam web
- Tanpa URL , Server dan Client tidak akan mengerti informasi apa yang ingin kita cari

URL nanti nya akan dibagi 2, pertama **domain** {header} nya dan satu lagi **contex path** {start line} nya 


### Anatomi URL

- URL terdiri dari beberapa bagian: 
- Beberapa bagian wajib ada, beberapa bagian lagi tidak wajib ada.
- Berikut adalah beberap contoh URL 
  - https://www.programmerzamannow.com/
  - https://www.programmerzamannow.com/premium-membership/
  - https://www.programmerzamannow.com/?search=java

#### Schema 
- Bagian awal dari URL adalah Schema yang mengidentifikasikan protokol yang perlu digunakan oleh Client
- Biasanya dalam url website, **schema** protocol nya adalah **http** dan **https**.

[![Schema.png](https://i.postimg.cc/xTHfMNp5/Schema.png)](https://postimg.cc/qzJHdqT6)

#### Authority

- Selanjutnya dipisahkan dengan tanda `://` diikuti dengan authority, yang terdiri dari domain dan nomor port yang pisahkan dengan `:`.
- Nama Domain nanti akan ditanyakan ke DNS untuk mendapatkan alamat IP nya 
- Namun kita juga bisa langsung menggunakan IP jika memang website tersebut tidak memiliki domain. 
- Nomor Port tidak wajib, tanpa nomor port secara default bernilai `80` untuk http dan `443` untuk https 

[![Authority.png](https://i.postimg.cc/nhJHkV6J/Authority.png)](https://postimg.cc/F7T5FvrW)

#### PATH (Context Path)

- Selanjut nya setelah Authority, bagian selanjut nya yang tidak wajib yaitu **path**
- Path biasanya berisikan informasi menuju resource yang kita tuju
- Path terlihat seperti kumpulan folder dan diakhiri dengan nama file yang kita ingin akses

[![Path.png](https://i.postimg.cc/wx1TxGhS/Path.png)](https://postimg.cc/QVrr0SYb)

#### Paramaters

- Selanjutnya dalam URL kita juga bisa temukan informasi **Parameters**, namun ini tidak wajib 
- Parameters dipisah oleh karakter `?` setelah Authority atau path.
- Parameters merupakan informasi tambahan yang berisi `key=value`, jika ingin menambahkan lebih dari satu parameter, kita bisa tambahkan parameters dengan menggunakan karakter `&`


#### Anchors

- Anchor merupakan bahgian yang tidak wajib di URL
- Anchor merupakan representasi dari bookmark dalam sebuah halaman website ditandai dengan tanda `#`
- Misalkan dalam sebuah website terdapat banyak sekali bagian informasi, kita bisa gunakan **Anchor** sebagai bookmark ke setiap bagian informasi tersbut agar lebih mudah di akses.

[![Anchors.png](https://i.postimg.cc/KYxdKRC1/Anchors.png)](https://postimg.cc/yDpftY1K)

## HTTP Heders

- HTTP Header merupakan informasi tambahan yang biasa dikirim di **Request** atau **Response**.
- HTTP Header biasa digunakan agar informasi tidak harus dikirim melalui **Request Body** atau **Response body**.
- HTTP Header berisi `key:value`dan saat ini sudah banyak sekali standarisasi nama key pada HTTP header.
- https://en.wikipedia.org/wiki/List_of_HTTP_header_fields

 ### Contoh HTTP Header
 

| HTTP Header     | Keterangan                                             |
|-----------------|--------------------------------------------------------|
| `Host`          | Autority pada URL (Wajib sejak versi http 1.1)         |
| `Content-Type`  | Tipe data dari HTTP body                               |
| `User-Agent`    | Informasi User Agent (browser dan sistem Operasi       |
| `Accept`        | Tipe data yang diterima oleh Client                    |
| `Authorization` | Cridential untuk authentikasi (misal username+password |




## HTTP Status

- HTTP Status merupakan kode **HTTP Response** yang mengindikasikan apakah sebuah request yang diterima server sukses, gagal atau ada hal2 lain yang perlu di ketahui disisi client 
- HTTP Status diklasifikasikan dalam lima group, yaitu :
  - Informational Response (100-199)
  - Successful Response (200-299)
  - Redirect (300-399)
  - Client Error (400-499)
  - Server Error (500-599)

### Informational Response (100-199)

- Informational Response mengidentifikasikan bahwa request telah di terima dan dimegerti.
- Namun Client diminta untuk menunggu tahap akhir response
- Pada kenyataannya, Informational response sangat jarang sekali di gunakan 

### Successful Response (200-299)

- Successful Response merupakan indikasi code bahwa request yang dikirim oleh client telah diterima, dimengerti dan sukses diproses oleh server.

### Redirect (300-399)

- Redirect status code merupakan indikasi bahwa client harus melakukan aksi selanjutnya untuk menyelesaikan request.
- Biasanya redirect status code digunakan ketika locaksi sebuah resource berubah, sehingga server meminta client untuk berpindah ke URL lain 

### Client Error (400-499)

- Client Erros status code merupakan indikasi bahwa request yang dikirim oleh Client tidak diterima oleh server dikarenakan request yang dikirim dianggap tidak valid 
- Contohnya Client mengirim body yang salah, client melakukan request tanpa authetikasi di resource yang mewajibkan authetikasi, dan lain2.


### Server Error (500-599)

- Server Error status code merupakan indikasi bahwa terjadi kesalah server 
- Biasanya ini terjadi ketika ada maalah di server, seperti misalanya tidak bisa terkoneksi ke basis data, terdapat jaringan error di server dan lain2


## HTTP Body

- HTTP Body merupakan data yang bisa dikirim di **HTTP Request**, atau data yang diterima dari **HTTP Response** (bolak balik)
- Artinya client bisa mengirim data ke server menggunakan HTTP Body, begitu juga sebaliknya (server ke client)
- Server bisa memberikan body di response menggunakan HTTP body. ---> **Content-type** di header
- 


### Content-Type 

- HTTP Body erat kaitannya dengan Header key **Content-Type**. 
- Biasanya agar Client dan Server mudah mengerti isi HTTP body, HTTP message akan memiliki **Header Content-Type**, yang berisi informasi tipe data HTTP Body.
- HTTP body bisa berisikan text (html, java-script, css, json) atau binary(image, video, audio)
- Data Content-Type sudah memiliki standarisasi.



## Redirect 

- Seperti yang sudah dijelaskan pada materi HTTP Status, untuk memaksa client melakukan redirect ke halaman lain. kita bisa menggunakan http direct status code (300-399)
- Lantas pertanyaannya, dari mana client tahu, harus melakukan redirect ke URL mana?
- Oleh Karena itu, biasanya response HTTP Status redirect, selalu dibarengin dengan informasi URL redirectnya, dan itu disimpan pada **header location**.
- 
[![Redirect-Response.jpg](https://i.postimg.cc/XvLt9n0Q/Redirect-Response.jpg)](https://postimg.cc/2qqHDRyZ)


## HTTP cookie

[flash back : Stateless]

  - HTTP didesin stateless, artinya tiap request yang dilakukan, dia tidak tahu request sebelumnya atau selanjutnya yang akan di lakukan.
  - Lantas pertanyaannya, Bagaimana Server tahu, kalo Client sudah login sebelum mengakses halam tertentu
  - Hal ini biasanya menggunakan fitur HTTP Cookies


**jadi HTTP cookie adalah :**

- HTTP Cookie merupakan informasi yang diberikan oleh server, dan client secara otomatis akan menyimpan data tersebut, contoh nya di WebBroser.
- Ketika Web Browser melakukan request selanjutnya, maka Web Browser akan menyisipkan cookie yang sudah diterima di request sebelum nya.
- Dari cookies tersebut, Server bisa mengetahui apakah request tersebut merupakan request client yang sudah login atau belum


### Cookie di HTTP Response 

- Informasi cookie yang diberikan dari server, Ditempatkan pada Header dengan value **set-Cookies**
- Cookie bisa lebih dari satu, jika server memberikan lebih dari satu cookie, bisa menggunakan beberapa key **Set-Cookie** di Header.
- inget cookie bisa dirubah oleh user ..jadi perlu untuk step validasi cookie

[![Cookie-Response.jpg](https://i.postimg.cc/RhykqGzm/Cookie-Response.jpg)](https://postimg.cc/rRGnP1mZ)

### Cookie di HTTP Request

- Setelah Cookie dari HTTP Response diterima oleh WebBrowser, maka akan disimpan di WebBrowser
- Selanjutnya HTTP Request selanjutnya akan mengirim **Cookie** di tiap request, dimana Cookie yang dikirim bisa menggunkan Header dan nama Cookie
- Berbeda dengan HTTP Response, HTTP Request, Cookie harus digabungkan di satu header jika lebih dari satu Cookie

[![Cookie-di-Request.jpg](https://i.postimg.cc/635JPyhk/Cookie-di-Request.jpg)](https://postimg.cc/PLcRpf9y)

### Cookie Attributes

- Cookie memiliki atribut yang bisa ditambahkan ketika membuat cookie di HTTP Response
- Seperti masa berlaku cookie, apakah harus HTTPS, apakah tidak boleh diakses via script, dan lain2

di lokasi storage web Broser 


[![Cookie-Attribute.jpg](https://i.postimg.cc/6QhxzdCV/Cookie-Attribute.jpg)](https://postimg.cc/2q3tSLc3)

## HTTP Caching

- HTTP memeiliki fitur yang bernama **Caching**.
- Caching adalah menimpan data di client sampai batas waktu yang sudah ditentukan, sehingga jika Client ingin melakukan request resource yang sama, cukup ambil resource nya di client, tanpa harus meminta ulang ke server.
- HTTP Caching sangat cocok dilakukan untuk resource file static yang jarang berubah, sperti file, gambar, audio, video dan lain2.

[![IMG-A2-F2-D6-D6-FE9-D-1.jpg](https://i.postimg.cc/NFKhgSSb/IMG-A2-F2-D6-D6-FE9-D-1.jpg)](https://postimg.cc/GTngK7cs)

### Header Cache Control

- Server ketika meminta agar client melakukan caching, maka HTTP Response perlu menambahkan informasi **Cache-Control** di Header
- Cache-Control berisi informasi seperti berapa **lama client bisa menyimpan data response tersebut** sehingga tidak perlu meminta ulang ke server.

[![Cache-control.png](https://i.postimg.cc/L5Y7dfgb/Cache-control.png)](https://postimg.cc/1VSMw8HG)

[![Caching-from-memory.png](https://i.postimg.cc/15Nxbxp3/Caching-from-memory.png)](https://postimg.cc/jLKkJFgp)


## Next Tech

- Server-Sent Event
- WebSocket
- Cross-Origin Resource Sharing
- RESTful API
- OAuth