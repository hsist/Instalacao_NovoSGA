# Configuração do painel de controle do NovoSGA
Após executar a linha "bin/console novosga:install", na instação dessa aplicação, o sistema criará um usuário e uma unidade, além de determinar a prioridade e nível de acesso do usuário. Esses regitros são essenciais para a utilização da aplicação.

## 1 - Acesso ao painel de configuração da aplicação
```
Acessar o novosga com as credenciais determinados no fim da instação da aplicação. Exemplo:
 - .../novosga/public
 - usuário: admin
 - senha: 123456
 ```
 
## 2 - Criar um serviço
 ```
 - Acesse a engrenagem na parte superior da página, lado direito: Administração;
 - Selecione a aba "Serviços";
 - Crie um serviço.
 ```
 
 ## 3 - Criar um serviço
 ```
 - Acesse a engrenagem na parte superior da página, lado direito: Administração;
 - Selecione a aba "Serviços";
 - Crie um serviço.
 ```
 
<hr>

# Configuração do painel de senhas do NovoSGA
Configuração para ligar o painel de controle com o painel de senhas.

## 1 - Ligar a aplicação com o painel
Entre em configurações, acesse a opção Web API e Adicione um Cliente. O sistema irá gerar um Id e um Client secret, essa credenciais deverão ser cadastradas no painel, pois é dessa forma que o novoSGA cria uma ligação com o painel (sistema de gerenciamento x painel). 
