# Proxy Corporativo para Linguagens de Programaçao
Configurando o proxy para ferramentas de linguagens de programaçao OpenSource, especialmente quando voce eh um cara macho e nao usa IDEs.

# 0. Introduçao



# 1. JAVA
## 1.0 Ferramenta Maven
Para fazer o 'maven' sair pela internet atraves de um proxy, va ate o diretorio do usuario e coloque as seguintes configuraçoes no arquivo '~/.m2/settings.xml'
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
## 1.1 Ferramenta Gradle
Para fazer o 'gradle' sair para internet atraves de um proxy, va ate o diretorio do usuario e coloque as seguintes configuraçoes no arquivo '~/.gradle/gradle.properties'
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


# 2. Frameworks JavaScripts NODE.js
## 2.1 Ferramenta NPM
Voce pode definir o endereço de proxy para a ferramenta 'NPM' a partir da linha de comando.
```bash
npm config set proxy http://nome_usuario:senha@endereco_ip:porta
npm config set https-proxy http://nome_usuario:senha@endereco_ip:porta
```
Voce tambem pode cadastrar o endereço do proxy para seu usuario, inserindo os valores diretamente no arquivo de configuraçao `~/.npmrc` que deve estar (ou ser criado) dentro do seu diretorio de usuario:
```xml
proxy=http://nome_usuario:senha@endereco_ip:porta
https-proxy=http://nome_usuario:senha@endereco_ip:porta
https_proxy=http://nome_usuario:senha@endereco_ip:porta
```

## 2.1 Ferramenta yarn


# 3. Python
## 3.1 Ferramenta pip

# 4. GIT
Voce pode definir o endereço de proxy para a ferramenta git a partir da linha de comando.
```bash
# Usando a linha de comando para proxy http
git config --global http.proxy http://nome_usuario:senha@endereco_ip:porta
# Usando a linha de comando para proxy https
git config --global https.proxy http://nome_usuario:senha@endereco_ip:porta
```
Voce tambem pode cadastrar o endereço do proxy para seu usuario, inserindo os valores diretamente no arquivo de configuraçao `~/.gitconfig` que deve estar (ou ser criado) dentro do seu diretorio de usuario:
```xml
[http]
        proxy = http://nome_usuario:senha@endereco_ip:porta
[https]
        proxy = http://nome_usuario:senha@endereco_ip:porta
```

# Referencias Bibliograficas
[JHipster - http://www.jhipster.tech/configuring-a-corporate-proxy/](http://www.jhipster.tech/configuring-a-corporate-proxy/)
