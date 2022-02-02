# The Cyber Plumbers Handbook

The definitive guide to SSH tunneling, port ,redirection and bending traffic like a Boss

## Basics
### SSH Server 

Konfigurasi untuk Service SSH berada pada directoru " /etc/ssh/sshd_config." ssh konfigurasi bisa kita validasi dengan menggunakan perintah : 

`/usr/sbin/sshd -t`

setiap perubahan pada file config SSH, maka dibutuhkan restart service tersebut agar perubahan dapat dikenali 

-  melihat status service ssh
`systemctl status ssh`

- Restart Service SSH
`systemctl restart ssh`

- Stop service SSH
`systemctl stop ssh` 

- Start service SSH
`systemctl start ssh`

### SSH Client

ssh client adalah pihak yang menggunakan service ssh untuk remote akses, berikut adalah opsi default pada service SHH

[ssh default option]

### Netcat 

Netcat tool (nc), bisa digunakan sebagai simple program untuk chatting, atau mengepush shell dari sebuah client ke server ato sebalik nya. untuk beberapa kasus setelah SSH tunnel tercreate kita menggunakan netcat untuk memvalidasi **basic network connectivity**, untuk netcat yang lebih komplit pastikan menginstall versi **netcat-openbsd** 

`apt install netcat-openbsd -y`

```
- l   Listen mode, for inbound traffic
- n   Supress name/port resolutions
- p   Specific Local port for remote connection
- u   UDP mode
- v   Verbose
```

**TCP mode** jika opsi -u tidak dicantumkan, ketika menggunakan netcat sebagai client (connecting to listening port) syntak perintah nya sbb:

`nc [destination] [port]`


## Networking Basic 
### Network interface Card (NIC)
Pada dasar nya, setiap server yang baru terdapa 2 jenis interface, 

**interface pertama** : digunakan untuk berkomunikasi ke node/server yang lain ada dalam jaringan yg terhubung biasa nya dinamakan dengan istilah **eth0** atau **ens33** atau dalam istilah umum disebut dengan **external interface**

**interface kedua*** : biasa nya digunakan untuk komunikasi internal server "localhost/127.0.0.1", Penting untuk bisa mengetahui perbedan dari dua jenis interface ketika ingin menghubungkan "pipes" antara dua mesin/lebih

### House Analogy 

sebuah analogy dapat kita pergunakan untuk menggambarkan computer sebagai rumah dan interface sebagai pintu

[network interface as house]

## SSH -L Port forward to 127.0.0.1
