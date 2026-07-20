
---
File Transfer Protocol é um dos protocolos mais antigos da internet, criado especificamente para a transferência de arquivos entre um cliente e servidor. 

Quando vc faz download ou upload de um arquivo usando um cliente FTP como o ( FileZilla ), o protocolo opera de uma forma muito específica e diferente da maioria dos outros protocolos da camada de aplicação ( como o HTTP )

A principal característica do FTP apresentada no livro é que ele utiliza duas conexões paralelas distintas para realizar o seu trabalho

### 1. Conexão de controle (Porta 21)
- Serve para enviar comandos de controle, como nome de usuário, senha, comandos para mudar de diretório(cd), ou comandos para listar, buscar ou enviar arquivos (get e put)
- Ela permanece aberta durante toda a seção do usuário 

### 2. Conexão de Dados (porta20)
- Serve exclusivamente para a transferência real dos arquivos 
- Diferente da conexão de controle, a conexão de dados é temporária: ela se abre quando um arquivo começa a ser transferido e se fecha assim que a transferência daquele arquivo terminar. Se você transferir outro arquivo em seguida, uma nova conexão de dados é aberta. 

### FTP é um protocolo "com estado " (Stateful)
Há um contraste importante entre HTTP e FTP:
- o HTTP é sem estado? o servidor não guarda um histórico dos seus pedidos anteriores (a menos que use cookies)
- o FTP é com estado: o servidor precisa manter o controle do estado do usuário. Ele lembra se vc já fez login, em qual diretório vc está navegando no momento e suas permissões de acesso. 
Manter o estado de cada usuário ativo limita a quantidade de clientes simultâneos que um servidor FTP consegue aguentar ao mesmo tempo se comparado a um servidor web comum. 