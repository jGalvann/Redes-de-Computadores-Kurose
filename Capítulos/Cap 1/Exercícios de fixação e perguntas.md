# Questões de Revisão — Capítulo 1

## Seção 1.1

**R1.** Qual é a diferença entre um hospedeiro e um sistema final? Cite os tipos de sistemas finais. Um Servidor Web é um sistema final?

**R2.** A palavra protocolo é muito usada para descrever relações diplomáticas. Como a Wikipédia descreve um protocolo diplomático?

**R3.** Por que os padrões são importantes para os protocolos?

---

## Seção 1.2

**R4.** Cite quatro tecnologias de acesso. Classifique cada uma delas nas categorias: acesso residencial, acesso corporativo ou acesso móvel.

**R5.** A taxa de transmissão HFC é dedicada ou é compartilhada entre usuários? É possível haver colisões na direção provedor-usuário de um canal HFC? Por quê?

**R6.** Cite as tecnologias de acesso residencial disponíveis em sua cidade. Para cada tipo de acesso, apresente a taxa *downstream*, a taxa *upstream* e o preço mensal anunciados.

**R7.** Qual é a taxa de transmissão de LANs Ethernet?

**R8.** Cite alguns meios físicos utilizados para instalar a Ethernet.

**R9.** HFC, DSL e FTTH são usados para acesso residencial. Para cada uma dessas tecnologias de acesso, cite uma faixa de taxas de transmissão e comente se a taxa de transmissão é compartilhada ou dedicada.

**R10.** Descreva as tecnologias de acesso sem fio mais populares atualmente. Faça uma comparação entre elas.

---

## Seção 1.3

**R11.** Suponha que exista exatamente um nó de comutação de pacotes entre um computador de origem e um de destino. As taxas de transmissão entre a máquina de origem e o comutador e entre este e a máquina de destino são $R_1$ e $R_2$, respectivamente. Admitindo que um roteador use comutação de pacotes do tipo armazena-e-reenvia, qual é o atraso total fim a fim para enviar um pacote de comprimento $L$? *(Desconsidere formação de fila, atraso de propagação e atraso de processamento.)*

**R12.** Qual é a vantagem de uma rede de comutação de circuitos em relação a uma de comutação de pacotes? Quais são as vantagens da TDM sobre a FDM em uma rede de comutação de circuitos?

**R13.** Suponha que usuários compartilhem um enlace de 2 Mbps e que cada usuário transmita continuamente a 1 Mbps, mas cada um deles transmite apenas 20% do tempo. *(Veja a discussão sobre multiplexação estatística na Seção 1.3.)*
- **a.** Quando a comutação de circuitos é utilizada, quantos usuários podem ser admitidos?
- **b.** Para o restante deste problema, suponha que seja utilizada a comutação de pacotes. Por que não haverá atraso de fila antes de um enlace se dois ou menos usuários transmitirem ao mesmo tempo? Por que haverá atraso de fila se três usuários transmitirem ao mesmo tempo?
- **c.** Determine a probabilidade de um dado usuário estar transmitindo.
- **d.** Suponha agora que haja três usuários. Determine a probabilidade de, a qualquer momento, os três usuários transmitirem simultaneamente. Determine a fração de tempo durante o qual a fila cresce.

**R14.** Por que dois ISPs no mesmo nível de hierarquia farão emparelhamento (*peering*)? Como um IXP consegue ter lucro?

**R15.** Alguns provedores de conteúdo criaram suas próprias redes. Descreva a rede da Google. O que motiva os provedores de conteúdo a criar essas redes?

---

## Seção 1.4

**R16.** Considere o envio de um pacote de uma máquina de origem a uma de destino por uma rota fixa. Relacione os componentes do atraso que formam o atraso fim a fim. Quais deles são constantes e quais são variáveis?

**R17.** Visite a animação interativa *"Transmission versus Propagation Delay"* no site de apoio do livro. Entre as taxas, o atraso de propagação e os tamanhos de pacote disponíveis, determine uma combinação para a qual o emissor termine de transmitir antes que o primeiro bit do pacote chegue ao receptor. Ache outra combinação para a qual o primeiro bit do pacote alcança o receptor antes que o emissor termine de transmitir.

**R18.** Quanto tempo um pacote de 1.000 bytes leva para se propagar através de um enlace de 2.500 km de distância, com uma velocidade de propagação de $2,5 \times 10^8 \text{ m/s}$ e uma taxa de transmissão de 2 Mbps? Em geral, quanto tempo um pacote de comprimento $L$ leva para se propagar através de um enlace de distância $d$, velocidade de propagação $s$, e taxa de transmissão de $R$ bps? Esse atraso depende do comprimento do pacote? Depende da taxa de transmissão?

**R19.** Suponha que o hospedeiro A queira enviar um arquivo grande para o hospedeiro B. O percurso de A para B possui três enlaces, de taxas $R_1 = 500 \text{ kbps}$, $R_2 = 2 \text{ Mbps}$ e $R_3 = 1 \text{ Mbps}$.
- **a.** Considerando que não haja nenhum outro tráfego na rede, qual é a vazão para a transferência de arquivo?
- **b.** Suponha que o arquivo tenha 4 milhões de bytes. Dividindo o tamanho do arquivo pela vazão, quanto tempo levará a transferência para o hospedeiro B?
- **c.** Repita os itens "a" e "b", mas agora com $R_2$ reduzido a 100 kbps.

**R20.** Suponha que o sistema final A queira enviar um arquivo grande para o sistema final B. Em um nível muito alto, descreva como o sistema A cria pacotes a partir do arquivo. Quando um desses arquivos chega ao roteador, quais informações no pacote o roteador utiliza para determinar o enlace através do qual o pacote é encaminhado? Por que a comutação de pacotes na Internet é semelhante a dirigir de uma cidade para outra pedindo informações ao longo do caminho?

**R21.** Visite a animação interativa *"Queuing and Loss"* no site de apoio do livro. Qual é a taxa de transmissão máxima e a taxa de transmissão mínima? Com essas taxas, qual é a intensidade do tráfego? Execute a animação interativa com essas taxas e determine o tempo que leva a ocorrência de uma perda de pacote. Repita o procedimento mais uma vez e determine de novo o tempo de ocorrência para a perda de pacote. Os resultados são diferentes? Por quê? Por que não?

---

## Seção 1.5

**R22.** Cite cinco tarefas que uma camada pode executar. É possível que uma (ou mais) dessas tarefas seja(m) realizada(s) por duas (ou mais) camadas?

**R23.** Quais são as cinco camadas da pilha de protocolos da Internet? Quais as principais responsabilidades de cada uma dessas camadas?

**R24.** O que é uma mensagem de camada de aplicação? Um segmento de camada de transporte? Um datagrama de camada de rede? Um quadro de camada de enlace?

**R25.** Quais camadas da pilha do protocolo da Internet um roteador processa? Quais camadas um switch processa? Quais camadas um sistema final processa?

---

## Seção 1.6

**R26.** O que é um *malware* autorreprodutivo?

**R27.** Descreva como pode ser criada uma *botnet* e como ela pode ser utilizada no ataque DDoS.

**R28.** Suponha que Alice e Bob estejam enviando pacotes um para o outro por uma rede de computadores e que Trudy se posicione na rede para poder capturar todos os pacotes enviados por Alice e enviar o que quiser para Bob; ela também consegue capturar todos os pacotes enviados por Bob e enviar o que quiser para Alice. Cite algumas atitudes maliciosas que Trudy pode fazer a partir de sua posição.