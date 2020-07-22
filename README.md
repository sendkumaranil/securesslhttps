# securesslhttps
Secure SSL and Https Example in Spring Boot
# Generate Self-signed-certificate
keytool -genkey -alias selfsigned_localhost_sslserver -keyalg RSA -keysize 2048 -validity 700 -keypass changeit -storepass changeit -keystore ssl-server.jks

![alt tag](https://github.com/sendkumaranil/securesslhttps/blob/master/Screenshot%202019-03-02%20at%2010.02.04%20PM.png)

# Generate Certificate Signed Request (CSR) by using jks
keytool -certreq -alias selfsigned_localhost_sslserver -file ssl-server.csr -keystore ssl-server.jks

you will get the csr file -> open file-> copy the text from -----BEGIN NEW CERTIFICATE REQUEST----- to -----END NEW CERTIFICATE REQUEST-----

<h4>Open https://getacert.com/signacert.html and paste copied text and submit</h4>
<h4>Download localhost-<timestamp>.cer and getacert.cer files</h4>
  
# Import the cer certificates to the JKS
<h4>First import the root certificate getacert.cer</h4>
keytool -import -alias getacert -file getacert.cer -keystore ssl-server.jks
<h4>Now import the localhost certificate</h4>
keytool -import -alias selfsigned_localhost_sslserver -file localhost-2020-07-22-065742.cer -keystore ssl-server.jks

# View certificate list
keytool -list -v -keystore ssl-server.jks

# Certificate Details
![alt tag](https://github.com/sendkumaranil/securesslhttps/blob/master/ssl-server-certificate.png)
