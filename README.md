# Tutorial - Como proteger seu Ubuntu com a autenticação de dois fatores do Google.

## Por que autenticar traz mais segurança?

Explicação...


## Start

Lembre-se de instalar o Google Authenticator em seu smartphone... Vamos começar!

#### Passo 1

Primeiramente é necessário instalar a libpam do google authenticator, ela que ira aplicar a autenticação na hora de realização do login no sistema.

```shell
sudo apt install libpam-google-authenticator
```
Aceite (Y) a utilização da memória pela aplicação e instale ela no sistema. 

#### Passo 2

O próximo passo é editar o arquivo de configuração da biblioteca pam. Vamos abrir o arquivo `common-auth` que esta localizado na pasta `/etc/pam.d/` com algum editor de texto (neste caso utilizei o vim):

```shell
cd /
sudo vim /etc/pam.d/commom-auth
```

Com o arquivo aberto adicione uma nova linha com o seguinte conteúdo: 

```shell
auth  required      pam_google_authenticator.so echo_verification_code
```

Salve o arquivo (no vim `:wq`).

#### Passo 3
