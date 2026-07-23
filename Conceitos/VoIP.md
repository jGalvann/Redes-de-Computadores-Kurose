
---
### VoIP (Voice over IP)

- **Definição:** Classe de aplicação de tempo real que transmite conversas de voz digitalizadas através da internet, em vez de usar a rede telefônica tradicional — é o exemplo clássico de aplicação **tolerante a perdas**, mas **sensível ao atraso**.
- **Por que usa [[UDP]] e não [[TCP]]:** Numa chamada de voz, um pacote perdido ou levemente corrompido é preferível a um pacote _atrasado_ — o ouvido humano tolera pequenas falhas no áudio, mas não tolera silêncios/travamentos. Como o [[TCP]] retransmite pacotes perdidos (o que gera atraso) e o [[UDP]] simplesmente não garante entrega, o VoIP roda sobre **[[Protocolos Não Orientados à Conexão|UDP]]**, priorizando velocidade sobre confiabilidade.
- **Sensibilidade à temporização:** É uma aplicação de tempo real clássica — precisa de baixo atraso fim a fim para manter a conversa fluida e natural. Isso está diretamente ligado ao **[[Atraso de fila]]**: se os pacotes de voz ficam presos demais no [[buffer]] dos roteadores no caminho, a chamada trava ou fica com "delay", mesmo que os pacotes cheguem intactos.
- **Jitter:** além do atraso em si, o VoIP também sofre com a _variação_ do atraso entre pacotes consecutivos — para compensar isso, o receptor costuma usar um pequeno buffer de reprodução que "segura" os pacotes por um instante antes de tocar o áudio, suavizando essa variação.
- **Ligações com outros conceitos:**
    - **[[Protocolos Não Orientados à Conexão]]:** VoIP é citado como exemplo direto de uso do UDP.
    - **[[Atraso de fila]] / [[buffer]]:** a principal ameaça à qualidade de uma chamada VoIP.