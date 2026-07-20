
---

Um **proxy** é um servidor intermediário que fica entre um cliente e o servidor de destino, recebendo as requisições do cliente e repassando-as (ou respondendo por conta própria) em nome dele. O cliente, em geral, nem percebe que está "conversando" com um intermediário — do ponto de vista dele, parece que a resposta veio direto do servidor de origem.

#### Por que usar um proxy?

- **Desempenho/Cache:** guardar cópias de recursos já acessados para responder mais rápido e economizar banda — é exatamente o papel do **[[Web Cache ( servidor proxy )]]**.
- **Privacidade/Anonimato:** esconder o endereço IP real do cliente do servidor de destino.
- **Controle de acesso/Filtragem:** empresas e escolas usam proxies para bloquear sites, monitorar tráfego ou aplicar políticas de rede.
- **Segurança:** atuar como uma camada extra entre a rede interna e a internet pública.

#### Tipos de proxy (visão geral)

- **Proxy direto (forward proxy):** fica do lado do **cliente** — ele intermedia as requisições que os clientes de uma rede fazem para a internet (ex: proxy de uma empresa controlando o acesso dos funcionários). É o tipo mais comum quando o assunto é [[Web Cache ( servidor proxy )]].
- **Proxy reverso (reverse proxy):** fica do lado do **servidor** — intermedia requisições que chegam da internet para um ou mais servidores internos, geralmente fazendo balanceamento de carga entre eles. Conceito próximo do que uma **[[CDN - Content Delivery Networks]]** faz em escala global.

#### Ligações com outros conceitos já vistos

- [[HTTP]]: o proxy web opera interceptando e retransmitindo requisições HTTP.
- [[Cache]]: cache é o "porquê" de existir boa parte dos proxies web.
- [[Get Condicional]]: é o mecanismo que o proxy usa para validar se sua cópia em cache ainda está atualizada, sem precisar rebaixar o objeto inteiro do servidor de origem.
- [[Socket]] / [[TCP]]: como qualquer intermediário de rede, o proxy também abre suas próprias conexões — uma com o cliente, outra com o servidor de origem quando necessário.