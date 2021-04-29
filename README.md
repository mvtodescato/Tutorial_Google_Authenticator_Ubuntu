# Tutorial - Como proteger seu Ubuntu com a autenticação de dois fatores do Google.

## Por que autenticar traz mais segurança?

Autenticar é o ato de confirmar algo como autêntico, ou seja, que reivindica a autoria ou a veracidade. Sendo assim, a autenticação se mostra importante sempre que é necessário segurança, principalmente quando tratamos de login para ter acesso a alguma informação ou ferramenta, sendo utilizada para verificar a identidade do usuário.

A autenticação normalmente depende de um ou mais "fatores de autenticação". Existem basicamente 3 tipos de mecanismos para isso. A autenticação baseada no conhecimento (login e senha), autenticação baseada na propriedade (token gerado em algum dispositivo que pertence ao usuário) e a autenticação baseada na característica (digital, por exemplo). Esses mecanismos contém brechas e falhas, sendo assim, combina-los garante uma segurança adicional. 

A autenticação de dois fatores pode conter esses três mecânimos. Login e senha são necessárias para acesso na grande maioria dos sistemas e utilizando um software como o Google Authenticator temos o token sendo gerado em um dispositivo do usuário que, na maioria das vezes, é protegido pelo acesso com a digital do mesmo. Sendo assim, temos uma garantia de segurança, sendo necessário ao possível invasor quebrar todos esses mecânismos.

Aqui então se encontra um tutorial simples de como proteger seu Ubuntu com a autenticação de dois fatores do Google:


## Ínicio

Lembre-se de instalar o Google Authenticator em seu smartphone e confirmar que seu computador está no mesmo fuso-horário do celular... Vamos começar!

#### Passo 1

Primeiramente é necessário instalar a libpam do google authenticator, ela que ira aplicar a autenticação na hora de realização do login no sistema.

```shell
sudo apt install libpam-google-authenticator
```
Aceite (Y) a utilização da memória pela aplicação e instale ela no sistema. 

#### Passo 2

O próximo passo é editar o arquivo de configuração da biblioteca pam. Vamos abrir o arquivo `common-auth` que esta localizado na pasta `/etc/pam.d/` com algum editor de texto (neste caso utilizei o vim):

```shell
sudo vim /etc/pam.d/commom-auth
```

Com o arquivo aberto adicione uma nova linha com o seguinte conteúdo: 

```shell
auth  required      pam_google_authenticator.so echo_verification_code
```

Salve o arquivo (no vim `:wq`).

#### Passo 3

Execute o google authenticator no sistema com o seguinte comando no terminal:

```shell
google-authenticator
```
Após isso aceite a autenticação baseada em tempo (Y). Será gerado um QR Code(juntamente com o código que ele representa) e os códigos de emergência. É recomendável anotar os códigos e salvar em algum lugar seguro. No aplicativo do Google Authenticator no seu smarthphone adicione um novo dispositivo lendo o QR Code ou colocando o código.

No terminal aceite ou recuse conforme suas preferências as configurações de login e finalize o processo.

A partir desse momento ao deslogar de seu usuário será necessário autenticar o login com o código de autenticação gerado pelo Google Authenticator no seu smartphone.
