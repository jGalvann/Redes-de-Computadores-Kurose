
---
### Protocolos de Aplicação

- **Definição:** Camada mais alta da pilha, a que interage diretamente com o usuário/software. Define os tipos de mensagem trocados entre os processos, a sintaxe de cada mensagem (quais campos existem), a semântica desses campos e as regras de quando/como um processo deve enviar e responder mensagens.
- **Como funcionam:** Rodam **dentro** dos sistemas finais (nunca nos roteadores do núcleo da rede) e se apoiam nos serviços oferecidos pela camada de transporte ([[TCP]] ou [[UDP]]) para efetivamente entregar as mensagens entre os [[Processo]]s, através de um [[Socket]].
- **Protocolo ≠ aplicação:** um protocolo de aplicação é só _uma parte_ de uma aplicação de rede maior — o [[HTTP]], por exemplo, é apenas o protocolo; a "aplicação Web" completa também envolve navegador, servidor, cache etc.
- **Uso comum:** cada protocolo resolve um problema específico de comunicação:
    - Navegação web → [[HTTP]] (roda sobre [[TCP]])
    - Transferência de arquivos → [[FTP]] (roda sobre [[TCP]])
    - Resolução de nomes → [[DNS]] (roda sobre [[UDP]])
    - Envio de e-mails → SMTP (roda sobre [[TCP]])
- _Exemplos:_ **[[HTTP]]** (páginas web), **[[FTP]]** (transferência de ficheiros), **[[DNS]]** (resolução de nomes), **SMTP** (envio de e-mails).
