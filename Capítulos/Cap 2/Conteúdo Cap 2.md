
---

> A partir daqui o livro muda de perspectiva: em vez de olhar a rede "de fora" (roteadores, núcleo, atraso), ele foca no topo da pilha — o que o desenvolvedor de aplicações efetivamente controla.

### 2.1 Princípios das Aplicações de Rede

- A grande sacada da camada de aplicação: para criar uma aplicação de rede, basta escrever programas que rodam em **sistemas finais diferentes** e conversam entre si trocando mensagens. Não é preciso escrever nada para os dispositivos do núcleo da rede (roteadores), porque eles não operam na camada de aplicação. Isso é o que permite o desenvolvimento rápido de novas aplicações.

#### 2.1.1 Arquiteturas de Aplicações de Rede

- **[[Cliente-servidor]]:** existe um servidor sempre ativo, com endereço IP fixo, que atende requisições de vários clientes. Os clientes não se comunicam diretamente entre si (ex: Web, [[FTP]]). Como um servidor único não escala, é comum usar **[[datacenter]]** com servidores virtuais para dar conta do volume de requisições.
- **P2P (peer-to-peer):** dependência mínima (ou nula) de servidores sempre ativos; os próprios sistemas finais (peers) conversam diretamente entre si. Vantagem: **autoescalabilidade** (cada novo peer traz também capacidade extra). Desvantagens: difícil de gerenciar, segurança e questões de ISP.

#### 2.1.2 Comunicação entre Processos

- Quem troca mensagens de fato não são "programas", são [[Processo]]s rodando dentro dos sistemas finais.
- Dois processos na mesma máquina se comunicam por mecanismos do próprio SO (fora do escopo do livro); processos em máquinas diferentes trocam mensagens **pela rede**.
- Todo processo envia/recebe mensagens da rede através de um [[Socket]] — a interface entre a aplicação e a camada de transporte.
- Em toda comunicação existe um processo **cliente** (o que inicia a comunicação) e um processo **servidor** (o que espera para ser contatado).
- Para endereçar um processo especificamente é preciso **dois** identificadores: o **endereço IP** (identifica o hospedeiro) e o **número de porta** (identifica o processo dentro daquele hospedeiro).

#### 2.1.3 Serviços de Transporte Disponíveis às Aplicações

Ao escolher um protocolo de transporte, uma aplicação tem que pensar em 4 dimensões de serviço:

- **Confiabilidade na transferência de dados:** algumas aplicações não podem tolerar perda de dados (transferência de arquivo, e-mail); outras toleram perda até certo ponto (áudio/vídeo em tempo real — chamadas "tolerantes a perdas").
- **Vazão (throughput):** aplicações **sensíveis à banda** (ex: streaming) precisam de uma taxa mínima garantida; aplicações **elásticas** (e-mail, transferência de arquivo, Web) se adaptam à banda disponível no momento.
- **Temporização (timing):** aplicações em tempo real (VoIP, jogos interativos) exigem baixo atraso fim a fim para não comprometer a experiência.
- **Segurança:** criptografia dos dados, integridade e autenticação das partes envolvidas.

#### 2.1.4 Serviços de Transporte Oferecidos pela Internet

- **[[TCP]]** ([[Protocolos Orientados à Conexão|orientado à conexão]]): entrega confiável, ordenada, com controle de fluxo e de congestionamento. É o que a maioria das aplicações "importantes" usa (Web, e-mail, transferência de arquivo).
- **[[UDP]]** ([[Protocolos Não Orientados à Conexão|não orientado à conexão]]): serviço leve, sem garantia de entrega, ordenação ou controle de congestionamento — por isso é rápido e usado onde velocidade/baixo atraso importa mais que confiabilidade.
- Nenhum dos dois oferece garantias de vazão mínima ou de atraso máximo — a internet "tradicional" é uma rede de **melhor esforço**.

#### 2.1.5 Protocolos de Camada de Aplicação

- Um **[[Protocolos de Aplicação|protocolo de aplicação]]** define: os tipos de mensagem trocados, a sintaxe de cada mensagem (quais campos existem), a semântica dos campos (o que cada campo significa) e as regras que dizem quando/como um processo envia e responde mensagens.
- **Protocolo de aplicação ≠ aplicação de rede:** o [[HTTP]] é só uma parte da "aplicação Web" (que também envolve navegador, servidor, formato dos documentos etc.).
- Exemplos que o livro aprofunda: [[HTTP]] (Web), SMTP (e-mail), [[DNS]] (nomes) — e, historicamente, [[FTP]] (transferência de arquivos).

---

### 2.2 A Web e o HTTP

- O **[[HTTP]]** (HyperText Transfer Protocol) é o protocolo de camada de aplicação da Web — implementado tanto no navegador (cliente) quanto no servidor Web. Roda sobre o **[[TCP]]** (herda a confiabilidade do transporte orientado à conexão).
- Uma página Web é um conjunto de **objetos** (HTML, imagens, vídeo, CSS...), cada um endereçável por uma URL.
- **HTTP é "sem estado" (stateless):** o servidor, por padrão, não guarda histórico de requisições anteriores de um cliente. Isso simplifica o design do servidor, mas exige mecanismos extras (como cookies) quando é preciso "lembrar" do usuário.

#### 2.2.1 / 2.2.2 Visão Geral e Conexões Persistentes x Não Persistentes

- **Não persistente:** cada objeto é transferido em uma conexão TCP separada — a conexão abre, transfere 1 objeto, fecha. Gera overhead (novo handshake TCP a cada objeto).
- **Persistente (padrão desde o HTTP/1.1):** o servidor deixa a conexão TCP aberta após responder, permitindo enviar vários objetos pela mesma conexão — reduz o atraso total de carregamento da página.

#### 2.2.3 Formato da Mensagem HTTP

- **Requisição:** linha de método (`GET`, `POST`, `HEAD`, `PUT`, `DELETE`...) + URL + versão, seguida de linhas de cabeçalho (`Host`, `Connection`, `User-Agent`...).
- **Resposta:** linha de status (`200 OK`, `404 Not Found`, `304 Not Modified` — ver [[Get Condicional]]) + linhas de cabeçalho + corpo (o objeto solicitado).

#### 2.2.4 Interação Usuário-Servidor: [[Cookies]]

- Mecanismo que permite ao servidor identificar/reconhecer um usuário mesmo o HTTP sendo sem estado.
- Funcionamento: o servidor envia um cabeçalho `Set-Cookie` na resposta → o navegador guarda esse cookie → em requisições futuras ao mesmo site, o navegador reenvia o cookie no cabeçalho `Cookie` → o servidor mantém um banco de dados relacionando cookies a informações do usuário.

#### 2.2.5 Cache Web

- Ver nota completa: [[Cache]]
- Um **[[Web Cache ( servidor proxy )]]** (também chamado servidor proxy) atende requisições HTTP no lugar do servidor de origem, guardando cópias de objetos já solicitados — reduz tempo de resposta e tráfego de saída.
- O **[[Get Condicional]]** é o mecanismo (`Last-Modified` / `If-Modified-Since`, resposta `304 Not Modified`) que permite ao cache validar se sua cópia continua atualizada sem precisar rebaixar o objeto inteiro.
- A evolução do conceito de cache para escala global é a **[[CDN - Content Delivery Networks]]**.

#### 2.2.6 HTTP/2 

- Principal objetivo é reduzir a latência percebida ao possibilitar [[Multiplexação por Divisão de Frequência (FDM)|Multiplexação]] e respostas em uma única conexão [[TCP]
- **Motivação:** mesmo com conexões persistentes, o HTTP/1.1 sofre de **head-of-line blocking (HOL) na aplicação** — os objetos são enviados um atrás do outro na mesma conexão, então um objeto grande/lento "trava a fila" e atrasa os que vêm depois. Usar várias conexões TCP em paralelo ajuda, mas gera overhead extra e problemas de justiça (fairness) com outros fluxos.
- **Ideia central do HTTP/2:** permitir que múltiplas trocas de requisição/resposta aconteçam **intercaladas** dentro de uma **única conexão TCP**.
- **Como funciona:**
    - Cada mensagem (requisição ou resposta) é dividida em **frames** (quadros).
    - Os frames de diferentes objetos são **intercalados** na mesma conexão e depois **remontados** no destino — assim um objeto grande não bloqueia totalmente os outros.
    - O servidor pode **priorizar** a ordem de envio dos frames de resposta, conforme a importância de cada objeto para renderizar a página.
    - **Server Push:** o servidor pode enviar objetos que ele já sabe que o cliente vai precisar, sem esperar o cliente pedir cada um individualmente (ex: ao pedir o HTML, o servidor já manda o CSS junto).
    - **Compressão de cabeçalhos (HPACK):** como cabeçalhos HTTP se repetem muito entre requisições, o HTTP/2 comprime esses cabeçalhos para economizar banda.
- **Limitação que sobra:** como o HTTP/2 ainda roda sobre **[[TCP]]**, ele continua sofrendo de **head-of-line blocking na camada de transporte** — se um segmento TCP se perde, _todos_ os streams multiplexados naquela conexão ficam bloqueados até a retransmissão, mesmo que só um deles dependesse daquele dado. Isso é o que motivou o **HTTP/3**, rodando sobre QUIC (baseado em UDP).

---

### 2.3 Correio Eletrônico na Internet

- Assim como o correio tradicional, o e-mail é **assíncrono**: as pessoas enviam e leem mensagens quando bem entendem, sem precisar estar "online" ao mesmo tempo.
- Três componentes principais: **agentes de usuário** (o "leitor de e-mail"), **servidores de correio** (mantêm as caixas de mensagens) e o protocolo **SMTP** (Simple Mail Transfer Protocol), que roda sobre [[TCP]] e transfere mensagens do servidor do remetente para o servidor do destinatário.
- **Protocolos de acesso ao correio** (o usuário final não fala [[SMTP]] diretamente com o próprio servidor para _ler_ e-mails): POP3, IMAP e acesso via HTTP (webmail).

---

### 2.4 DNS — O Serviço de Diretório da Internet

#### 2.4.1 Serviços Fornecidos pelo DNS

- O **[[DNS]]** (Domain Name System) traduz nomes de domínio legíveis por humanos (ex: `google.com`) em [[IP|endereços IP]], já que é assim que hospedeiros e roteadores realmente se identificam na rede.
- É implementado como **(1)** um banco de dados distribuído em uma hierarquia de servidores DNS e **(2)** um protocolo de camada de aplicação que permite aos hospedeiros consultar esse banco (roda sobre [[UDP]], porta 53).
- Também é usado por outras aplicações para funções indiretas, como **balanceamento de carga** entre servidores replicados — é assim, por exemplo, que uma **[[CDN - Content Delivery Networks|CDN]]** direciona o usuário ao servidor de [[cache]] mais próximo dele.

#### 2.4.2 Visão Geral de Como o DNS Funciona

- Um único servidor DNS centralizado seria inviável: ponto único de falha, volume gigantesco de tráfego, distância geográfica de todo mundo e dificuldade de manutenção. Por isso o DNS é **distribuído e hierárquico**.
- Hierarquia de servidores:
    1. **Servidores raiz (root):** topo da hierarquia.
    2. **Servidores TLD (Top-Level Domain):** um conjunto para cada domínio de topo (`.com`, `.org`, `.br`...).
    3. **Servidores com autoridade (authoritative):** guardam os registros DNS reais de uma organização/domínio específico.
- **Servidor DNS local:** não faz parte estritamente da hierarquia acima, mas atua como intermediário das consultas de cada hospedeiro (em geral, é o servidor do próprio provedor/ISP), e costuma fazer **cache** das respostas.
- Uma consulta pode ser:
    - **Recursiva:** o servidor consultado assume a responsabilidade de obter a resposta final, e devolve só o resultado.
    - **Iterativa:** o servidor consultado devolve o endereço do próximo servidor a perguntar, e quem originou a consulta vai seguindo a cadeia sozinho.
- **Cache no DNS:** servidores guardam respostas de consultas recentes por um tempo (TTL) — acelera bastante as buscas seguintes e reduz o volume de mensagens DNS trafegando pela rede.

#### 2.4.3 Registros e Mensagens DNS

- Os servidores DNS guardam **Registros de Recursos (RR — Resource Records)**, cada um no formato `(Nome, Valor, Tipo, TTL)`.
- Principais tipos de registro:
    - **Tipo A:** `Nome` = nome do hospedeiro, `Valor` = endereço IP correspondente.
    - **Tipo NS:** `Nome` = domínio, `Valor` = nome do hospedeiro que roda o servidor com autoridade daquele domínio — usado para seguir a cadeia da hierarquia.
    - **Tipo CNAME:** `Valor` = nome canônico do hospedeiro, para quando `Nome` é um apelido (alias).
    - **Tipo MX:** `Valor` = nome canônico do servidor de e-mail associado ao alias `Nome`.
- **Mensagens DNS:** requisições e respostas compartilham o mesmo formato — um cabeçalho (com número de identificação e flags como "é consulta ou resposta" / "recursão desejada") seguido de seções de perguntas e de respostas (contendo os RRs).