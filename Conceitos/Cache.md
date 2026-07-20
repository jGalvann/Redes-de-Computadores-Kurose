
# Caching na Web e Relacionados

O **Cache** é um mecanismo de armazenamento temporário de dados acessados com frequência. O seu grande objetivo é **evitar trabalho repetido** para economizar tempo e recursos.

Na Web, a lógica é simples: se um arquivo (como uma foto ou uma folha de estilos CSS) não mudou, por que o seu computador precisa baixá-lo do servidor principal do outro lado do mundo toda vez que você atualiza a página? É muito mais rápido carregá-lo de uma memória local mais próxima.

- [[Web Cache ( servidor proxy )]]
- [[CDN - Content Delivery Networks]]
- [[Get Condicional]] 

## Resumo para Fixação:

- **Cache:** Guardar dados perto do usuário para responder mais rápido.
    
- **Web Cache / Proxy:** Servidor intermediário que guarda dados da web para acelerar o acesso de uma rede inteira.
    
- **GET Condicional (`304 Not Modified`):** A técnica que o protocolo usa para perguntar ao servidor se a cópia salva no cache ainda serve, evitando downloads repetidos.
    
- **CDN:** Uma rede mundial de caches gigantescos para entregar conteúdo de forma rápida, não importa onde o usuário esteja.

