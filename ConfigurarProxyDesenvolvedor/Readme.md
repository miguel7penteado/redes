# Proxy Corporativo para Linguagens de Programaçao
Configurando o proxy para ferramentas de linguagens de programaçao OpenSource, especialmente quando voce eh um cara macho e nao usa IDEs.

# 0. Introduçao
Normalmente, as aplicaçoes oriundas do Linux (talvez seja uma pratica em todo universo POSIX) procuram o caminho do proxy em 3 **variaves de ambiente** definidas previamente no shell que ira executar a ferramenta:
* 1. 'HTTP_PROXY' - Caminho do proxy utilizado em chamdas via protocolo **http**.
* 2. 'HTTPS_PROXY' - Caminho do proxy utilizado em chamdas via protocolo **https**.
* 3. 'FTP_PROXY' - Caminho do proxy utilizado em chamdas via protocolo **ftp**.

Mas com o advento de linguagens que acompanham um frameworks e suas ferramentas, tais como java, javascript e python, a forma de definir o endereço de um servidor proxy ficou relativa a cada uma delas. A seguir temos um resumo.

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
Para fazer a ferramenta 'yarn' ir buscar pacotes na internet atraves de um proxy, use a seguinte linha de comando:
```bash
yarn config set proxy http://nome_usuario:senha@endereco_ip:porta
yarn config set https-proxy http://nome_usuario:senha@endereco_ip:porta
```

# 3. Python
## 3.1 Ferramenta pip
Para fazer a ferramenta 'pip' buscar modulos python na internet atraves de um proxy, utilize a sguinte linha de comando:
```bash
#para http
python -m pip install --proxy http://nome_usuario:senha@endereco_ip:porta numpy
# para https
python -m pip install --proxy https://nome_usuario:senha@endereco_ip:porta numpy
```

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
