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
