# Proxy Corporativo para Linguagens de Programaçao
Configurando o proxy para ferramentas de linguagens de programaçao OpenSource, especialmente quando voce eh um cara macho e nao usa IDEs.

# 0. Introduçao



# 1. JAVA
## 1.0 Maven
No maven, va ate o diretorio do usuario e coloque as seguintes configuraçoes no arquivo ~/.m2/settings.xml
```xml
<proxies>
    <proxy>
        <id>id</id>
        <active>true</active>
        <protocol>http</protocol>
        <username>meu_usuario</username>
        <password>minha_senha</password>
        <host>endereço</host>
        <port>porta</port>
        <nonProxyHosts>local.net|some.host.com</nonProxyHosts>
    </proxy>
</proxies>
```
## 1.1 Gradle
No maven, va ate o diretorio do usuario e coloque as seguintes configuraçoes no arquivo ~/.gradle/gradle.properties
```bash
## Proxy setup
systemProp.proxySet="true"
systemProp.http.keepAlive="true"
systemProp.http.proxyHost=host
systemProp.http.proxyPort=port
systemProp.http.proxyUser=username
systemProp.http.proxyPassword=password
systemProp.http.nonProxyHosts=local.net|some.host.com

systemProp.https.keepAlive="true"
systemProp.https.proxyHost=host
systemProp.https.proxyPort=port
systemProp.https.proxyUser=username
systemProp.https.proxyPassword=password
systemProp.https.nonProxyHosts=local.net|some.host.com
## end of proxy setup
```


# 2. Frameworks JavaScripts

# 3. Python

# Referencias Bibliograficas
[JHipster - http://www.jhipster.tech/configuring-a-corporate-proxy/](http://www.jhipster.tech/configuring-a-corporate-proxy/)
