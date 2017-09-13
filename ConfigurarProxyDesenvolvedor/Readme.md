# Proxy Corporativo para Linguagens de Programaçao
Configurando o proxy para ferramentas de linguagens de programaçao OpenSource, caso comum quando voce eh aquele cabra macho que nao depende de `IDE`s para fazer seu serviço.

# 0. Introduçao
Normalmente, as aplicaçoes oriundas do Linux (talvez seja uma pratica em todo universo POSIX) procuram o caminho do proxy em 3 **variaves de ambiente** definidas previamente no shell que ira executar a ferramenta:
* 1. `HTTP_PROXY` - Caminho do proxy utilizado em chamdas via protocolo **http**.
* 2. `HTTPS_PROXY` - Caminho do proxy utilizado em chamdas via protocolo **https**.
* 3. `FTP_PROXY` - Caminho do proxy utilizado em chamdas via protocolo **ftp**.

Mas com o advento de linguagens que acompanham um frameworks e suas ferramentas, tais como java, javascript e python, a forma de definir o endereço de um servidor proxy ficou relativa a cada uma delas. A seguir temos um resumo.

# 1. JAVA
### 1.0 Ferramenta Maven
Para fazer o `maven` sair pela internet atraves de um proxy, va ate o diretorio do usuario e coloque as seguintes configuraçoes no arquivo `~/.m2/settings.xml`:
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
### 1.1 Ferramenta Gradle
Para fazer o `gradle` sair para internet atraves de um proxy, va ate o diretorio do usuario e coloque as seguintes configuraçoes no arquivo `~/.gradle/gradle.properties`
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


# 2. Framework JavaScripts NODE.js
O framework `Node.js` possui uma ferramenta de gestao de modulos chamada NPM (Node Package Manager) que acessa a internet para baixar versoes recentes de modulos, como eh o caso, por exemplo do React Native. Segue a forma de configurar o endereço de um servidor proxy para essa ferramenta acessar a internet.
### 2.0 Ferramenta NPM
Voce pode definir o endereço de proxy para a ferramenta `NPM` a partir da linha de comando.
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

### 2.1 Ferramenta yarn
Para fazer a ferramenta `yarn` ir buscar pacotes na internet atraves de um proxy, use a seguinte linha de comando:
```bash
yarn config set proxy http://nome_usuario:senha@endereco_ip:porta
yarn config set https-proxy http://nome_usuario:senha@endereco_ip:porta
```

# 3. Python
### 3.1 Ferramenta pip
Para fazer a ferramenta `pip` buscar modulos python na internet atraves de um proxy, utilize a sguinte linha de comando:
```bash
#para http
python -m pip install --proxy http://nome_usuario:senha@endereco_ip:porta numpy
# para https
python -m pip install --proxy https://nome_usuario:senha@endereco_ip:porta numpy
```

# 4. Ferramentas autonomas ou nao relacionadas a um Framework ou linuguagem especificos
### 4.1 GIT - Selecionar um proxy
Voce pode definir o endereço de proxy para a ferramenta `git` a partir da linha de comando.
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
### 4.2 GIT - excluir o proxy
Você também pode precisar remover do git as configurações de uso seu proxy da rede por motivos especificos

Metodo padrão: excluindo amigavelmente 
```bash
# afeta todos os usuarios
git config --global --unset https.proxy
git config --global --unset http.proxy
git config --global --unset https.proxy
# afeta apenas o usuario local
git config --local --unset https.proxy
git config --local --unset http.proxy
git config --local --unset https.proxy
```
Metodo 2 : Caso não funcione o método anterior, sua instalação de git pode ter fixado o proxy nos arquivos de configuração. Não se preocupe, faça o seguinte:

Linux
```bash
export GIT_TRACE=1
export GIT_CURL_VERBOSE=1
```
windows
```cmd
set GIT_TRACE=1
set GIT_CURL_VERBOSE=1
```

```bash
# descubra onde esta o arquivo de configuracao do git
git config --list --show-origin
```
Edite o arquivo mostrado ( por exemplo gitconfig) e exclua a linha que contem o endereço de proxy

# Referencias Bibliograficas
[JHipster - http://www.jhipster.tech/configuring-a-corporate-proxy/](http://www.jhipster.tech/configuring-a-corporate-proxy/)
[msysgit - Git-and-Proxy-Servers](https://github.com/msysgit/msysgit/wiki/Git-and-Proxy-Servers)
[StackoverFlow - Remove git proxy](https://stackoverflow.com/questions/32268986/git-how-to-remove-proxy)
