
---

### 1.1 Internet 

Inicialmente comenta por cima sobre a estrutura, sobre interações entre ISPs ( internet Service Providers ) 

> Quando um sistema final possui dados para enviar a outro sistema final, o sistema emissor segimenta esses dados e adiciona bytes de cabeçalho a cada segmento 

Também cita brevemente os [[protocolos de Rede]] [[TCP]] e [[IP]]. O protocolo IP especifica o formato dos pacotes que são enviados e recebidos entre os roteadores e sistemas finais. Os principais protocolos da internet são conhecidos como TCP/IP. 

### 1.1.3 Protocolos 

O livro abrange os conceitos iniciais de protocolo e a definição do mesmo. 

> Um. protocolo define o formato e a ordem das mensagem trocadas entre duas ou mais entidades comunicantes, bem como as ações realizadas na transmissão e/ou recebimento de uma mensagem ou outro evento. 

### 1.2 A Borda da Rede (Network Edge)

* **Sistemas Finais (End Systems) / Hospedeiros (Hosts):** Computadores, smartphones, servidores e dispositivos IoT que ficam na "borda" da internet (onde as aplicações rodam). Eles são divididos em:
    * *Clientes (Clients):* Dispositivos que requisitam serviços (ex: seu navegador).
    * *Servidores (Servers):* Máquinas que armazenam e distribuem dados (ex: páginas web, fluxos de vídeo).
* **Redes de Acesso (Access Networks):** Os meios físicos que conectam um sistema final ao seu primeiro roteador (roteador de borda). O livro detalha três cenários principais:
    1. *Acesso Residencial:* Evolução do [[DSL]] (usa linhas telefônicas) e Cabo (HFC - usa infraestrutura de TV a cabo com fibra e cabo coaxial compartilhados), até chegar no FTTH (Fibra para o Lar).
    2. *Acesso Institucional (Empresas/Universidades):* Uso de redes locais ([[LANs]]), predominantemente Ethernet, com [[switches ( comutadores da área de enlace )]] e roteadores conectados à internet.
    3. *Acesso Móvel:* Redes sem fio baseadas em pontos de acesso (Wi-Fi para curtas distâncias) e redes celulares (3G, 4G, 5G através de torres de telefonia).
* **Meios de Transmissão Físicos:** O caminho por onde os bits viajam, divididos em:
    * *Meios Guiados:* Sinais seguem um caminho físico (par trançado de cobre, cabo coaxial, fibra óptica).
    * *Meios Não Guiados:* Sinais se propagam livremente na atmosfera/espaço (Rádio, Wi-Fi, Satélite).

---

### 1.3 O Núcleo da Rede (Network Core)

* **Definição:** A malha de roteadores interconectados que formam a espinha dorsal da internet, responsável por mover os dados de uma borda à outra.

#### 1.3.1 Comutação de Pacotes vs. Comutação de Circuitos

* **[[Comutação de Pacotes]] (Packet Switching):**
    * Os dados das aplicações são divididos em **pacotes**. Cada pacote viaja de forma independente pelos enlaces de comunicação e comutadores (roteadores e switches).
    * Usa o princípio de **Transmissão Store-and-Forward (Armazena e Repassa):** O roteador precisa receber o pacote inteiro e verificar seus bits antes de começar a transmiti-lo para o próximo enlace.
    * **Filas e Perda de Pacotes:** Se a taxa de chegada de pacotes em um enlace for maior que a capacidade de transmissão dele, os pacotes extras entram em uma fila ([[buffer]]). Se a fila encher, ocorre o descarte de pacotes (perda).
* **[[Comutação de Circuitos]] (Circuit Switching):**
    * Os recrsos necessários ao longo do caminho para prover comunicação são **reservados** de forma dedicada para a sessão entre os sistemas finais (modelo tradicional da rede telefônica).
    * Garante desempenho constante, mas pode ser ineficiente (recursos ficam ociosos se não houver transmissão ativa).
    * Organizado através de **[[Multiplexação por Divisão de Frequência (FDM)]]** ou [[Multiplexação por Divisão de Frequência (FDM)]].

#### 1.3.2 Como os Pacotes Percorrem as Redes de Comutadores de Pacotes

* **A Jornada do Pacote:** Cada pacote contém em seu cabeçalho o endereço IP de destino. Quando um pacote chega a um roteador, este examina o endereço e consulta uma tabela interna para decidir para onde enviá-lo.
* **As Duas Funções Centrais do Núcleo da Rede:**
    1. **Repasse (Forwarding):** É a ação local e de curto prazo do roteador. Quando um pacote chega a uma linha de entrada, o roteador deve movê-lo para a linha de saída apropriada.
    2. **Roteamento (Routing):** É o processo global e de longo prazo da rede. Envolve algoritmos que determinam o caminho total (a rota) que os pacotes devem seguir da origem até o destino final.
* **Analogia Clássica:** O *Repasse* é como um carro que chega a um cruzamento e decide virar à direita; o *Roteamento* é como o processo de planejar a viagem inteira usando um mapa ou GPS.

#### 1.3.4 ISPs e Backbones da Internet

- A internet pública segue uma hierarquia de [[ISP]]s,  Existindo 3 níveis do mesmo, nivel 1, 2 e 3. 
- ISPs de nível 1 conectam-se diretamente a cada um dos outros ISPs de nível 1
- ISPs de nivel 1 conectam-se a um grande número de ISPs de nível 2 e outras redes clientes. 
- tem cobertura internacional.

---

### 1.4 Atraso, Perda e Vazão em Redes de Comutação de Pacotes

#### 1.4.1 Uma visão geral de atraso em redes de comutação de pacotes

Quatro componentes do **atraso nodal** (em cada roteador/salto):

- **Atraso de processamento (d_proc):** tempo para examinar o cabeçalho do pacote e decidir para onde enviá-lo (inclui verificação de erros de bit). Ordem de microssegundos.
- **[[Atraso de fila]] (d_fila):** tempo esperando no [[buffer]] de saída até poder ser transmitido. Varia MUITO — depende do nível de congestionamento.
- **Atraso de transmissão (d_trans = L/R):** tempo para "empurrar" todos os L bits do pacote para o enlace, a uma taxa R. Depende do **tamanho do pacote** e da **taxa do enlace**, não da distância.
- **Atraso de propagação (d_prop = d/s):** tempo para um bit viajar fisicamente pelo enlace (distância d, velocidade de propagação s, próxima da velocidade da luz). Depende da **distância**, não do tamanho do pacote.

> Pegadinha clássica de prova: transmissão ≠ propagação. Um ajuda a entender melhor a diferença, é imaginar um comboio de carros passando por um pedágio (analogia do livro).

Atraso nodal total = d_proc + d_fila + d_trans + d_prop

#### 1.4.2 Atraso de fila e perda de pacote

- **Intensidade de tráfego** = La/R, onde:
  - L = tamanho do pacote
  - a = taxa média de chegada de pacotes
  - R = taxa de transmissão do enlace
- Se La/R > 1 → fila cresce sem limite (atraso → infinito, no modelo idealizado).
- Se La/R se aproxima de 1 → atraso médio de fila cresce muito rápido (não linear).
- Como o [[buffer]] tem capacidade **finita**, na prática o que acontece é **perda de pacote** (buffer overflow) quando a fila enche.

#### 1.4.3 Atraso fim a fim

- Soma dos atrasos nodais ao longo de todo o caminho.
- **Traceroute:** ferramenta que mede o atraso de ida e volta (RTT) até cada roteador no caminho até o destino, enviando pacotes com TTL crescente.

#### 1.4.4 Vazão nas redes de computadores

- **Vazão instantânea:** taxa (bits/s) em um dado momento.
- **Vazão média:** F/T (F = tamanho do arquivo, T = tempo total de transferência).
- A vazão fim a fim é limitada pelo **enlace de gargalo** (bottleneck link) — o de menor taxa de transmissão em todo o caminho.
- Quando vários fluxos compartilham um enlace, a taxa de transmissão desse enlace é dividida entre eles → gargalo pode não ser mais só a rede de acesso.

---

### 1.5 Camadas de Protocolo e Modelos de Serviço

#### 1.5.1 Arquitetura de camadas

- Motivação: sistema complexo → dividir em módulos torna mais fácil de projetar, manter e modificar (mudar a implementação de uma camada sem afetar as outras, desde que a interface de serviço se mantenha igual).
- Desvantagem possível: duplicação de funcionalidade entre camadas (ex: controle de erro em várias camadas).

**Pilha de 5 camadas da Internet** (de cima pra baixo):

| Camada     | Unidade de dados | Exemplos                             |
| ---------- | ---------------- | ------------------------------------ |
| Aplicação  | mensagem         | [[HTTP]], [[SMTP]], [[FTP]], [[DNS]] |
| Transporte | segmento         | [[TCP]], [[UDP]]                     |
| Rede       | datagrama        | [[IP]]                               |
| Enlace     | quadro           | [[Ethernet]], [[WiFi]]               |
| Física     | bits             | —                                    |

- Cada camada oferece serviço à camada de cima usando os serviços da camada de baixo (**modelo de serviço**).
- **Hospedeiros** implementam as 5 camadas.
- **Roteadores** só até a camada 3 (rede).
- **[[switches ( comutadores da área de enlace )]]** só até a camada 2 (enlace).
- → complexidade da Internet está concentrada nas bordas (hospedeiros), não no núcleo.

#### 1.5.2 Encapsulamento

- Cada camada pega a PDU da camada de cima e **encapsula**: adiciona seu próprio cabeçalho → forma a carga útil (payload) da camada de baixo.
- Fluxo: mensagem → segmento → datagrama → quadro → bits.
- No destino, o processo é revertido (desencapsulamento), camada por camada, de baixo pra cima.

---

### 1.6 Redes sob Ameaça (Segurança)

- **Malware:** pode se autorreplicar (worm) ou precisar de interação do usuário (vírus). Pode instalar spyware, criar backdoors.
- **Botnet:** rede de hospedeiros comprometidos, controlados remotamente — usada em spam e ataques DDoS.
- **Ataques de recusa de serviço (DoS):** três tipos principais:
  - **Ataque de vulnerabilidade:** mensagens malformadas exploram falha no software/SO.
  - **Inundação de largura de banda:** sobrecarrega o enlace de acesso do alvo com volume de pacotes.
  - **Inundação de conexão:** esgota recursos com muitas conexões TCP semiabertas/abertas.
  - **DDoS (distribuído):** feito a partir de múltiplas fontes (ex: botnet) simultaneamente — muito mais difícil de mitigar.
- **Análise de pacotes (packet sniffing):** receptor passivo copia todo pacote que passa pelo meio — funciona bem em redes de difusão (ex: WiFi) e é difícil de detectar (não injeta nada na rede).
- **Disfarce da origem / IP spoofing:** criar pacote com endereço de origem falso.
- Consequência: precisamos de **autenticação de ponto final** — mecanismo pra garantir que uma mensagem realmente veio de quem diz ter vindo (tema aprofundado no capítulo de segurança).

---

### 1.7 História das Redes de Computadores e da Internet

- **1961–1972 — Nascimento da comutação de pacotes:** Kleinrock (teoria de filas, MIT), Baran (Rand), Davies/Scantlebury (NPL). 1969: primeiro roteador de pacotes na UCLA → nasce a ARPAnet.
- **1972–1980 — Redes proprietárias e interligação:** surgem ALOHAnet, redes por satélite/rádio da DARPA, Telenet, Cyclades, SNA (IBM). Cerf & Kahn criam o [[protocolos de Rede|TCP/IP]] (interconectar redes diferentes = "internetting").
- **1980–1990 — Proliferação de redes:** 1º jan. 1983, TCP/IP vira padrão oficial da ARPAnet. Surge o [[DNS]]. NSFNET conecta universidades (56 kbits/s → 1,5 Mbits/s).
- **1990s — Explosão da Internet:** ARPAnet se aposenta. Nasce a **World Wide Web** (Tim Berners-Lee, CERN, 1989–1991: HTML, HTTP, servidor e navegador). Popularização via Mosaic/Netscape.
- **Novo milênio:** banda larga residencial, acesso sem fio onipresente (WiFi, 3G/4G/5G), redes sociais, computação em nuvem, streaming de vídeo dominando o tráfego.