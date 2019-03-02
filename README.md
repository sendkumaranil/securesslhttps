# securesslhttps
Secure SSL and Https Example in Spring Boot
# Generate Self-signed-certificate
keytool -genkey -alias selfsigned_localhost_sslserver -keyalg RSA -keysize 2048 -validity 700 -keypass changeit -storepass changeit -keystore ssl-server.jks

