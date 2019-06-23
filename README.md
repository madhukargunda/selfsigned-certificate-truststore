# selfsigned-certificate-truststore
Generation of the self signed certificate and store into separate truststore file.


```


 1.Download the certificate from the client URL using browser

 2.Using keytool export certificate

 	keytool -export -alias myclient -keystore myclientstore.jks -rfc -file publickey.cert
 	keytool -list -keystore myclientstore.jks

 3.Adding the certificate in to JDK cacerts

 	keytool -importcert -alias myclient -keystore  cacerts -storepass changeit -file c:\work\cert\publickey.cer
 	keytool -list -keystore cacerts

 4.Creating own trustore from JDKTrust store

 	keytool -importKeystore -srckeystore cacerts -destkeystore mytruststore -deststoretype JKS 
 	keytool -list -keystore mytruststore

 5.

 	export keystoreFile=server.jks
    export keystoreType=JCEKS
    export keystorePass=password
    export keyAlias=server


 6. Create a private Public key pair with keytool

 	keytool -keystore ${keystoreFile} -storetype ${keystoreType:-JKS} -storepass ${keystorePass} -exportcert -alias ${keyAlias} -rfc -file idx.pem


 7.Validating the pem file

   openssl X509 -in idx.pem -text

 8.Importing public key into cacerts

 	keytool -importcert -file iddex.pem -keystore ${JAVA_HOME}/lib/security/cacerts -alias "myix" -storepass changeit
```


```
Generating the 2048 bit privatekye (domain.key ) and CSR (domain.csr) from scratch

  open req -newkey rsa:2048 -nodes -keyout domain.key -out domain.csr 

```

### Open SSL Generating a 2048 bit RSA Key

```
Step1 : Generating the key pair (public and private key)

openssl genrsa -des3 -out private.pem 2048

Generating RSA private key, 2048 bit long modulus
..+++
.......+++
e is 65537 (0x10001)
Enter pass phrase for private.pem:
Verifying - Enter pass phrase for private.pem:


- The above command generates the RSA keypair
- Keys are encrypted with the password
- The format of the private.pem file 

-----BEGIN RSA PRIVATE KEY-----
Proc-Type: 4,ENCRYPTED
DEK-Info: DES-EDE3-CBC,E63436239789D552

NukQu5D9R+1XiWOvmMTjkBggDpsO3haMBEsVUfVk8BlmSKPKfIKpNZ1M1AC8FDbp
1QpdYa6lnM0wyBoLbU5BCI4ZQR2Av81WUJMzMf1FtD1dU/6EFayzMATuAfHrFnFZ
aIosPu9T0/BGbS/BL9yVXet06BoOv4qJ/afQPg/swkGGizH7s3+z/Yo5qPopBDu7
dJymPC5IttVOLsOvh08zT8KDgSDUhIz0OpX2Lw4N0ewBrzF/XQQyA9b+3V1CRAWp
EiYkCrrBgTLE1OsNfpkDWeT4Ia2pKdX2Rn/zlmnBXeyVXXtwPluROXl+Kd4fKOVU
r6Ehr8Rn+L2qL9D7T54xDlrWVBhouT3ibFQm3tZTPjkL2A75xwC8e29WfpEHb/ip
4Q1ityrAIJOW4KcbdyThu25SxQOhEzgaEtUPl/3I0U/J5Om9ey1cIowiPWYcvEvm
X1seddqOPeGnG1CYFCyX91r2qgv+htPmdvo4OZZRhnbqm9M9JF3WTiLm92EGnkWC
WNDSPu7hmN1iDTtKWjlGhtDLvNYuBgj08Mk7cWOrBzTkWiCYV5K+cIQ3+Nyq/Vfu
mF39hhv7wMEhmgnEt0Rj6WpOwdjQX2aM0w+RZxsm76tivU6Kd9kLOs/puqZqhKn4
w7lo0cX76KgUVj/ZS48kpz+Q/fFiRjpiFwlaxdTcSodcvF/xnrB17vrjhKBhK/id
60alYk6JUjPSyM1aDfOkjzPENp/hXCYxAVlCe665q+nvqyFWJY3QYUJGG6IFjV0k
7Osujj2CEIZsN1thsPOYkFaOPdiJ9/I/03aNdPHBfWz2n4xR06aKPO5EhWb3VmOv
YQ0afn0IMZGoEnuwARAyvBC9IxE7STND1M54n+I14IemvzSZRdpsLf9kZw/+Sbto
dh22V2ua1BziEddr+O0qgi4EDODTwT3jBxsUPubNXXulSIqaMwCoIyrW0ZzR+e/N
lMmkoV7GjW2bXinYhXkE3wjEyHFgA0G1g/boZOCTpO2rZHdIetv3i8ZnFmwpVN0T
JtLkEcHxCuO6TR8T2+0lbJK0AEABxh77ti8+oWdtDU/6eaXt9FGfgGGsxH56oMaa
Zy9h1Lep/xpPjR+6f+eJ4pxkpBhuzBUl/8HadjUl01c2gYEGecY+M/MjdN02nB5v
biGet6APoSwZ9t2MQpDD3XFujtoek2ZCiAMkvdIXEDOGHhxCS/VPfh/f+QQLt2Y4
8YMWfDIijmKic961NWyMd2OYf8PwS1rGDvO72cgIekzyHjvmi0kX7POz9vl5voMz
2bvqJR2VuZEr7+Nntf38z+g5PX4a0ynH9ICi8VKq0YEXB6naVuVFdcT/yQJxnkvx
3iezOhBuKu2YODuLZGFYVr//9Y+iEKi9e+G2zDPa6qOZc6dP8TSoFk94G1aL5ymS
Qeyw8q05ynb8sOkFncoQ9b4WuI4DfQCQwZPaBEKQ/iMEX4/z6a9OfY1m6F9hVmqZ
vXaV1+zzGSWrQ6gZyHjCMZ0tdPJpHvK0ZGArJ2u6F1Hir7HEHO0YsYAv8F59krSZ
W50N6E2Exhzo8BXnoiFqkVzKRXQ4AQBRQCfkNbp5DMDzztlMAZ7RpTKOJQXyO0hs
-----END RSA PRIVATE KEY-----


Step2 : Extracting the public key to file

openssl rsa -in private.pem -outform PEM -pubout -out public.pem

  -pubout flag 
  
Step3 : Generating the unencrypted version of the 

openssl rsa -in private.pem -out private_unencrypted.pem -outform PEM

```

### RSA Key Generation, Signatures and Encryption using OpenSSL

```
What ever we are doing  using the java we can do with openssl 

USER A Public and private key 

1.Generate the public and private key 

		openssl version


 openssl genpkey -algorithm RSA -pkeyopt rsa_keygen_bits:2018 -pkeyopt rsa_keygen_pubexp:3  -out privkey-A.pem

   This generates the private key in Base64 format.


 2.openssl pkey -in privkey-A.pem -text 

    This displays the all the values  of the certificate in Hex decimal values.


 3.Creating the public key 

 	openssl pkey -in privkey-A.pem -out pubkey-A.pem -pubout

 	  This generates the public key in base 64 format


User B Publickey and Privatekey 

4.Generate the public and private key 

		openssl version


 openssl genpkey -algorithm RSA -pkeyopt rsa_keygen_bits:2018 -pkeyopt rsa_keygen_pubexp:3  -out privkey-B.pem

   This generates the private key in Base64 format.


 5.openssl pkey -in privkey-B.pem -text 

    This displays the all the values  of the certificate in Hex decimal values.


 6.Creating the public key 

 	openssl pkey -in privkey-B.pem -out pubkey-B.pem -pubout

 	  This generates the public key in base 64 format



 7.
     openssl pkey -in pubkey-A.pem -pubin -text 
     openssl pkey -in pubkey-B.pem -pubin -text 
    

     Displays the base64

 5. Create a the text file with the data

 6.openssl dgst -sha1 message.txt 

 7.openssl dgst -sha1 -sign privkey-A.pem -out signature.bin message.txt

     Here we are doing 

     	1.Generating the message digest
     	2.Encrypt the message digest using private key.

 8. Encrypt the message using the public key of the User B
    Encrypt the message using the UserB public key

   openssl pkeyutl -encrypt -in message.txt -pubin -inkey pubkey-b.pem -out ciphertext.bin

 
 9. openssl pkeyutl -decrypt -in ciphertext.bin -inkey privatkey-B.pem - out received-message.txt 


 10.openssl dgst -sha1 -verify pubkey-A.pem -signature signature.bin received-message.txt
 ```
