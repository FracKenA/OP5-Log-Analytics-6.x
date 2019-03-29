# Configure SSL suport for AD authentication.

## Export Certificate from Active Directory
1. Open the certificate manager on the AD server.

![](/media/media/image78_js.png)

2. Select the certificate and open it

![](/media/media/image79_js.png)

3. Select the option of copying to a file in the Details tab

![](/media/media/image80_js.png)

4. Click the Next button

![](/media/media/image81.png)

5. Keep the setting as shown below and click Next

![](/media/media/image82.png)

6. Keep the setting as shown below and click Next.

![](/media/media/image83.png)

7. Give the certificate a name

![](/media/media/image84.png)

8. After the certificate is exported, this certificate should be imported into a trusted certificate file that will be used by the Elasticsearch plugin.


## Import Certificate into Java Keystore

To import a certificate into a trusted certificate file, a tool called `keytool` which is located in the JDK installation directory.
  
Use the following command to import a certificate file changing the path to your SSL Certificate.
`keytool -import -alias YOUR_AD_DOMAIN_FQDN -storepass SUPER_SECRET_PASSWORD -file PATH_TO_CERTIFICATE -keystore /PATH_YOU/WANT_TO_STORE/keystore.jks`
 

You will be asked to set a password for the trusted certificate store. Remember this password, because it must be set in the configuration of the Elasticsearch plugin. The following settings must be set in the `elasticsearch.yml` configuration for
### SSL:
```
# SSL Certificate Store for LDAP/AD.
ssl.keystore.file: "/PATH_YOU/WANT_TO_STORE/keystore.jks"
ssl.keystore.password: "SUPER_SECRET_PASSWORD"
```
