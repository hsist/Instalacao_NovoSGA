# Configuração do painel de controle do NovoSGA
Após executar a linha "bin/console novosga:install", na instação dessa aplicação, o sistema criará um usuário e uma unidade, além de determinar a prioridade e nível de acesso do usuário. Esses regitros são essenciais para a utilização da aplicação.

## 1 - Acesso ao painel de configuração da aplicação
Acessar o novosga com as credenciais determinados no fim da instação da aplicação. Exemplo:
```
- .../novosga/public
- usuário: admin
- senha: 123456
```
 
## 2 - Criar um serviço
```
- Acesse a engrenagem na parte superior direita da página: Administração;
- Selecione a aba "Serviços";
- Crie um serviço.
```
 
## 3 - Ligar o serviço ao guichê
```
- Acesse a unidade na parte superior esquerda da página: Unidade (Unit);
- Selecione "Configurações";
- Abra a aba "Atendimento";
- Selecione o(s) serviço(s) e em seguida clique em "+" para adicionar ao guichê.
```
 
## 4 - Criar token de acesso
```
- Acesse a engrenagem na parte superior direita da página: Administração;
- Selecione a opção Web API;
- Adicione um Cliente. 
```
O sistema irá gerar um "Id" e um "Client secret", essas credenciais deverão ser cadastradas no painel, pois é dessa forma que o novoSGA cria uma ligação com o painel (sistema de gerenciamento x painel).
 
<hr>

# Configuração do painel de senhas do NovoSGA
Configuração para ligar o painel de controle com o painel de senhas.

## 1 - Ligar a aplicação com o painel
Ao acessar o painel de senhas pela primeira vez a aplicação levará o usuário a tela de configuração, caso isso não ocorra acesse: .../#/settings
```
- Na aba "Interface" altere o idioma para "Português";
- Selecione a aba "Servidor" e preencha os campos;
- "Servidor" recebe a URL onde a aplicação foi instalada (painel adm do novoSGA) => .../novosga/public;
- "Usuário" recebe o usuário criado na instalação da aplicação => admin;
- "Senha" recebe a senha do usuário informado acima;
- "Client Id" recebe o código (Id) gerado no item 4 da configuração do painel adm;
- "Client Secret" recebe o código (Client secret) gerado no item 4 da configuração do painel adm.
```
Ao salvar esses dados o usuário deve obter uma mensagem de sucesso, caso isso não ocorra, revise as informações inseridas.

## 2 - Ligar o painel a unidade e selecionar os serviços
Após efetivar a conexão do painel adm com o painel de senhas o usuário precisa determinar uma unidade para o painel e selecionar os serviços que serão exibidos.
```
- Clique em "Serviços";
- Selecione uma unidade;
- Marque o(s) serviço(s).
```
