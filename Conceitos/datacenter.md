
---
### Datacenter (Data Center)

Um **datacenter** é uma instalação física que concentra um número enorme de servidores (de milhares a centenas de milhares de máquinas), interligados por uma rede interna de altíssima velocidade, junto com toda a infraestrutura de energia, refrigeração e redundância necessária para mantê-los rodando 24/7.

#### Por que eles existem

- A arquitetura **[[Protocolos de Aplicação|cliente-servidor]]** exige um servidor sempre ativo — mas um único servidor físico não aguenta o volume de requisições de aplicações como Google, Netflix ou Instagram. A solução é substituir "um servidor" por milhares de servidores virtuais trabalhando em conjunto dentro de um datacenter.
- Serve tanto para **escalar horizontalmente** (adicionar mais máquinas conforme a demanda cresce) quanto para dar **redundância** (se uma máquina falha, outra assume).

#### Estrutura interna (visão geral)

- Os servidores ficam organizados em **racks**, conectados por switches de alta velocidade.
- Existe um **balanceador de carga** na entrada do datacenter, responsável por distribuir as requisições recebidas entre os servidores disponíveis, sem que o cliente perceba qual máquina específica o atendeu.
- A rede interna do datacenter é projetada para ter baixíssimo atraso e alta banda entre os próprios servidores, já que eles trocam dados constantemente entre si (não só com o mundo externo).

#### Ligações com outros conceitos já vistos

- **[[Protocolos de Aplicação]] (arquitetura cliente-servidor):** o datacenter é a materialização física do "servidor sempre ativo" — na prática, não é uma máquina, é um exército delas.
- **[[CDN - Content Delivery Networks]]:** uma CDN nada mais é do que **vários datacenters menores espalhados geograficamente**, em vez de um datacenter gigante centralizado — cada um funcionando como um ponto de cache/distribuição regional.
- **[[Web Cache ( servidor proxy )]] / [[Proxy]]:** dentro (ou na borda) de um datacenter, é comum haver servidores de cache/proxy para reduzir a carga sobre os servidores "reais" de aplicação.
- **[[DNS]]:** é frequentemente o DNS quem decide, na prática, para qual datacenter/servidor específico a requisição de um usuário deve ser direcionada (parte do balanceamento de carga em escala global).
- [[Cliente-servidor]]