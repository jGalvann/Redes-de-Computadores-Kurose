
---
## O que é um protocolo?

Um **protocolo** é um conjunto de regras e convenções que determina como dois ou mais dispositivos na rede comunicam entre si.

No livro, a definição formal é:

> _"Um protocolo define o formato e a ordem das mensagens enviadas e recebidas entre duas ou mais entidades de rede, bem como as ações realizadas na transmissão e/ou no recebimento de uma mensagem."_

- **A analogia humana:** Um protocolo de rede funciona exatamente como um protocolo social. Se você quer perguntar as horas a alguém na rua, você primeiro diz "Olá!" (espera a pessoa responder), depois pergunta "Que horas são?" e a pessoa responde. Se você apenas gritasse "HORAS!" sem seguir esse protocolo social, a comunicação provavelmente falharia.
---

## 2. A Diferença: Protocolos vs. Tipos de Protocolos

A grande diferença é que **um protocolo é uma implementação específica** (como uma receita com passos exatos), enquanto os **tipos de protocolos** são as categorias, camadas ou propósitos aos quais essas regras pertencem.

Podemos classificar os protocolos principalmente de duas formas: **por função (o que fazem)** e **por camada (onde atuam)**.

### A. Classificação por Função (O que eles garantem?)

Os protocolos de transporte (como os que você verá logo após a página 90) dividem-se principalmente em dois grandes tipos de comportamento:

1. [[Protocolos Orientados à Conexão]] (ex: [[TCP]]):
    
2. **[[Protocolos Não Orientados à Conexão]] (ex: [[UDP]]):**

### B. Classificação por Camadas (Onde eles atuam?)

A pilha de protocolos da internet (o modelo TCP/IP que você está a estudar no Capítulo 1) organiza os tipos de protocolos em camadas. Cada camada tem protocolos específicos para resolver um problema de cada vez:

- **[[Protocolos de Aplicação]] (Interagem com o utilizador/software):**
    
- **[[Protocolos de Transporte]] (Cuidam da entrega entre processos):**
    
- **[[Protocolos de Rede]] (Cuidam do encaminhamento dos pacotes pela internet):**
    
- **[[Protocolos de Enlace]] (Cuidam da transmissão de dados entre dispositivos vizinhos na mesma rede física):**