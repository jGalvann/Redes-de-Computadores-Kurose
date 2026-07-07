
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
    * Organizado através de **[[Multiplexação por Divisão de Frequência (FDM)]]** ou [[**Multiplexação por Divisão de Tempo (TDM)]]**.

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

