# Open SSL

## Getting Started
there entry point for the OpenSSL Library is the open SSL binary usually /usr/bin/openssl on linux

''' $ openssl command [ command_option ] [ command argument ]'''





----------------------------------------------------------------------



## Generate key OpenSSL

* Generate the Private key ( RSA 2048)

```
openssl genrsa -aes128 -out fd.key 2048
```

* how to lock paramater private key

```
openssl rsa -text -in fd.key
```

* DSA key generation is 2 step process (step 1 : DSA parameter , step 2 : DSA key )

```
openssl dsaparam -genkey 2048 | openssl dsa -out dsa.key -aes128 
```

* ECDSA (256 bit) same is 2 step like DSA

```
openssl ecparam -genkey -name secp256r1 | openssl ec -out ec.key -aes128
```

## Create Certificate Signing Request (CSR)

once you have private keys, you can processes to create CSR , This is formal request asking a CA to sign a Certificate

```
openssl req -new -key fd.key -out fd.csr 

or 

openssl req -new -key dsa.key -out dsa.csr 

or 

openssl req -new -key ec.key -out ec.csr 
```

* create csr from exiting certificate

```
openssl x509 -x509toreq -in fd.csr out fd.csr -signkey fd.key 
```

* uattended CSR generatio
using costum openssl configuration file ( .cnf ) so the process will automatic


```
[req]
prompt = no
distinguished_name = dn
req_extensions = ext
input_password = PASSPHRASE

[dn]
CN = www.feistyduck.com
emailAddress = webmaster@feistyduck.com
O = Feisty Duck Ltd
L = London
C = GB
[ext]
subjectAltName = DNS:www.feistyduck.com,DNS:feistyduck.com
```

```
openssl req -new -config fd.cnf -key fd,key -out fd.csr 
```

* signing your own certificate


```
openssl x509 -req -days 365 -in fd.csr -signkey fd.key -out fd.crt
```

* 


### Examining Certificates

the x509 command does just to upack the cert , -text with to print certificate content , -noout to reduce cluster by not printing the encode certificate itself

```
openssl x509 -text -in fd.crt -noout 
```

### Extract information from the CSR

```
$ openssl req -in shellhacks.com.csr -text -noout
```

### Verify the signature

```
$ openssl req -in shellhacks.com.csr -noout -verify
```

### Whom the certificate will be issued to?

```
$ openssl req -in shellhacks.com.csr -noout -subject
```

### Show the public key

```
$ openssl req -in shellhacks.com.csr -noout -pubkey
```

### To decode from Base64:

```
openssl base64 -d -in &lt;infile&gt; -out &lt;outfile&gt;
```

Conversely, to

## encode

to Base64:

```
openssl base64 -in &lt;infile&gt; -out &lt;outfile&gt;
```

## Verify the Chain of CA

```
openssl verify -verbose -CAfile RootCert.pem Intermediate.pem
```

full chain

```
openssl verify -CAfile RootCert.pem -untrusted Intermediate.pem UserCert.pem
```

```
or 
openssl verify -verbose -CAfile &lt;(cat Intermediate.pem RootCert.pem) UserCert.pem
```

respon crl

```
openssl x509 -text -noout -in PrivyIDPersonalSignCAG1.pem
```

### Check Ocsp Validation

```
openssl ocsp -issuer Personal1-chain.pem -cert OCSPTest1.pem -CAfile Personal1-chain.pem -nonce -text -url &lt;http://10.8.20.6:8080/ejbca/publicweb/status/ocsp&gt;

 openssl ocsp -issuer PrivyIDPersonalSignCAG1.cacert.pem -cert OCSPTestPersonalCA.pem -CAfile PrivyIDPersonalSignCAG1-chain.pem -nonce -text -url &lt;http://10.8.20.6:8080/ejbca/publicweb/status/ocsp&gt;
```

super valid

```
 openssl ocsp -issuer PrivyCAClass2G1.pem -cert IsNewTest1.pem -CAfile PrivyCAClass2G1-chain.pem -nonce -text -url &lt;https://ocsp-uat.privyca.id
```

## Ekstrak key

openssl pkcs12 -in PKCS12file -out keys_out.txt

### P12 Properties

* p12 dump information

```
openssl pkcs12 -info -in INFILE.p12 -nodes
```

* Encrypted the private key
If you would like to encrypt the private key and protect it with a password before output, simply omit the -nodes flag from the command:

```
openssl pkcs12 -info -in INFILE.p12 -nodes
```

### **Extract Only Certificates or Private Key**

If you only want to output the private key, add -nocerts to the command:

```
openssl pkcs12 -info -in aaron__russell.p12 -nodes -nocerts
```

If you only need the certificates, use -nokeys (and since we aren’t concerned with the private key we can also safely omit -nodes):

```
openssl pkcs12 -info -in INFILE.p12 -nokeys
```

## Save Certificates and Private Keys to Files

You can export the certificates and private key from a PKCS#12 file and save them in PEM format to a new file by specifying an output filename:

```
openssl pkcs12 -in INFILE.p12 -out OUTFILE.crt -nodes
```

Again, you will be prompted for the PKCS#12 file’s password. As before, you can encrypt the private key by removing the -nodes flag from the command and/or add -nocerts or -nokeys to output only the private key or certificates. So, to generate a private key file, we can use this command:

```
openssl pkcs12 -in INFILE.p12 -out OUTFILE.key -nodes -nocerts
```