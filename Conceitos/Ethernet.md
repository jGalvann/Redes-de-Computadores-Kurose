
---
### Ethernet

- **Definição:** Protocolo de [[Protocolos de Enlace|camada de enlace]] dominante em redes cabeadas — é o padrão que define como os quadros (frames) são formatados e transmitidos entre dispositivos dentro de uma mesma [[LANs|LAN]].
- **Endereçamento MAC:** Cada interface de rede tem um **endereço MAC** (físico, gravado de fábrica na placa), diferente do [[IP]] (lógico, atribuído pela rede). O Ethernet usa o endereço MAC para entregar o quadro ao dispositivo certo _dentro_ da rede local — a tradução entre IP e MAC é feita por outro protocolo, o ARP.
- **Estrutura em quadros (frames):** Os dados vindos da camada de rede são encapsulados num quadro Ethernet, que contém: endereço MAC de destino, endereço MAC de origem, um campo de tipo (indicando o protocolo da camada superior) e o payload de dados.
- **Topologia atual:** Hoje em dia, uma rede Ethernet é organizada em estrela, com um [[switches ( comutadores da área de enlace )|switch]] no centro interligando todos os hosts — diferente das versões antigas, que usavam um cabo compartilhado (barramento) onde todos os dispositivos "escutavam" o mesmo meio físico.
- **Ligação com outros conceitos:**
    - **[[LANs]]:** Ethernet é a tecnologia que efetivamente implementa a maioria das LANs cabeadas.
    - **[[switches ( comutadores da área de enlace )]]:** são os dispositivos que interligam os hosts de uma rede Ethernet, usando os endereços MAC para decidir por qual porta encaminhar cada quadro.
    - **[[roteador]]:** enquanto o Ethernet/switch resolve a entrega _dentro_ da LAN (camada de enlace), é o roteador quem decide como o tráfego sai _entre_ redes diferentes (camada de rede).