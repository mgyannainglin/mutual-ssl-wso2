# mutual-ssl-wso2

1. Generat the ssl with cert extension.
2. Add generated ssl in mutual ssl options at respective api.
     * give the alias name for cert
     * choose http and https options
     * choose gateway in environment and redeploy that api
3. Add generate cert into wso2 gateway **client-truststore-jks**.
4. Add mutual ssl option in gateway **configmap**
```
 [apimgt.mutual_ssl]
 certificate_header = "SSL-CLIENT-CERT"
 enable_client_validation = false
 client_certificate_encode = false
```
***default ssl header name*** "X-WSO2-CLIENT-CERTIFICATE"

5. encrypt the exported ssl with base64 and add that value in your postman.
   ```
   base64 exported.cert > base64-text.txt
   ```

6. After all changes complete and correct.
   * restart the respective wso2 **gateway** pod
   * restat the respective wso2 **key-manager** pod

[wso2-ref-url](https://apim.docs.wso2.com/en/latest/design/api-security/api-authentication/secure-apis-using-mutual-ssl/)
