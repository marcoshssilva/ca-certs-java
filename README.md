# ca-certs-java
# Import Certify as Trusted for Java
Used to update my java certs from agents connected in https://app-jk.marcoshssilva.com.br, and describe how to import cert in Java using Keytool

> This is for fix PKIX path building failed:
> sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target

---
## Install

1. Verify if you contain Keytool in your machine
```
keytool -help
```

1. Verify if your **$JAVA_HOME** is set, if not, export it:
   > You can skip this, if you use absolute path to your JDK/JRE home
   ```
   $JAVA_HOME/bin/java --version
   ```

2. Import your CRT or PEM file to default CACERTS from JVM
   ```
   keytool -importcert -alias YOUR_ALIAS_NAME -keystore $JAVA_HOME/lib/security/cacerts -file /path/to/certificate.crt|pem
   ```
   Example:
   ```
   keytool -importcert -alias my-cert -keystore $JAVA_HOME/lib/security/cacerts -file /home/myuser/certificate.crt
   ```
   > You be asked for store-pass, usually, is 'changeit' for default JVM, but check if you have access.
---
## Remove Cert

To remove your cert, just remove your alias.
Command:
```
keytool -delete -noprompt -alias ${cert.alias}  -keystore ${keystore.file} -storepass ${keystore.pass}
```

Example:
```
keytool -delete -noprompt -alias my-cert -keystore $JAVA_HOME/lib/security/cacerts -storepass changeit
```
