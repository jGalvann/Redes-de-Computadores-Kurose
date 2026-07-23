
---
### Protocolos de Enlace

- **Definição:** Cuidam da transmissão de dados entre dispositivos **vizinhos** dentro da mesma rede física (o mesmo "enlace" — cabo, fibra ou canal sem fio) — ou seja, atuam no salto local, e não na entrega fim a fim entre origem e destino final.
- **Como funcionam:** Pegam o pacote entregue pela camada de rede e o encapsulam num **quadro (frame)**, adicionando endereçamento **MAC** (endereço físico, diferente do [[IP]]) para identificar os dispositivos dentro daquele enlace específico. Cada salto da rede (de switch em switch, de roteador em roteador) pode inclusive usar um protocolo de enlace diferente.
- **Uso comum:** Toda a comunicação dentro de uma [[LANs|LAN]] — redes cabeadas de escritório, campus, residência (via [[Ethernet]]) ou redes sem fio (via Wi-Fi/802.11).
- **Dispositivos associados:** É a camada em que operam os [[switches ( comutadores da área de enlace )|switches]], responsáveis por encaminhar os quadros dentro da mesma rede local usando endereços MAC — diferente do [[roteador]], que trabalha uma camada acima (rede), olhando endereços IP para levar dados _entre_ redes diferentes.
- _Exemplos:_ **[[Ethernet]]**, **Wi-Fi** (802.11).