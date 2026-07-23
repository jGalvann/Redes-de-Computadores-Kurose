
---
### Protocolos de Transporte

- **Definição:** Camada responsável por levar as mensagens da camada de aplicação de um **processo** para outro, entre os sistemas finais — ou seja, cuida da entrega **fim a fim entre processos** (diferente da camada de enlace, que cuida só do salto local).
- **Como funcionam:** Cada processo se comunica com a camada de transporte através de um [[Socket]]. A camada de transporte usa o **número de porta** (junto com o [[IP]] do hospedeiro) para entregar os dados ao processo correto na máquina de destino. Antes de enviar, ela decide qual "tipo" de serviço usar, considerando as 4 dimensões vistas em [[Protocolos de Aplicação|2.1.3]]: confiabilidade, vazão, temporização e segurança.
- **Os dois grandes tipos:**
    - **[[Protocolos Orientados à Conexão]]** — fazem handshake antes de trocar dados, garantem entrega confiável e ordenada.
    - **[[Protocolos Não Orientados à Conexão]]** — enviam direto, sem handshake nem garantias, priorizando velocidade.
- **Uso comum:** É a camada usada por praticamente toda a comunicação da internet — Web, e-mail, transferência de arquivo, chamadas de voz/vídeo, jogos online — cada aplicação escolhendo o protocolo de transporte de acordo com suas necessidades.
- _Exemplos:_ **[[TCP]]** (entrega fiável) e **[[UDP]]** (entrega rápida).
