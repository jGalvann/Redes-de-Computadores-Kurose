
Um **Web Cache** (frequentemente chamado de **Servidor Proxy**) é uma entidade de rede que atende a requisições HTTP em nome do servidor Web de origem. Ele mantém cópias de objetos recentemente solicitados em seu próprio armazenamento.
### Como funciona o fluxo de requisições:

1. O navegador do usuário envia uma requisição HTTP para o Web Cache.

2. **Hit (Acerto):** Se o objeto solicitado estiver guardado no cache e estiver atualizado, o Web Cache retorna o objeto imediatamente para o cliente.

3. **Miss (Erro/Falta):** Se o objeto não estiver no cache, o Web Cache abre uma conexão com o servidor de origem (o servidor real do site), baixa o objeto, guarda uma cópia em seu disco local e o entrega para o usuário final.

### Por que usamos isso na infraestrutura da Web?

- **Reduz o tempo de resposta:** O cache geralmente está muito mais próximo geograficamente do usuário do que o servidor de origem (por exemplo, dentro da rede do seu provedor de internet ou na sua própria rede corporativa).

- **Reduz o tráfego de saída:** Diminui drasticamente o gargalo nos links de internet das empresas e das operadoras.

- **Alivia os servidores principais:** Impede que servidores de grandes portais caiam por excesso de requisições simultâneas.
