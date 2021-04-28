# Tutorial - Como proteger seu Ubuntu com a autenticação de dois fatores do Google.

## Por que autenticar traz mais segurança?

Explicação...


## Start

Lembre-se de instalar o Google Authenticator em seu smartphone... Vamos começar!

### Passo 1

Primeiramente é necessário instalar a libpam do google authenticator, ela que ira aplicar a autenticação na hora de realização do login no sistema.

```shell
sudo apt install libpam-google-authenticator
```
