
---

Um [[Processo]] envia mensagens para a rede e recebe mensagens dela através de uma interface de software denominada **SOCKET**.

Para entender de forma simples, o livro faz uma analogia clássica:
- O **Processo** é como uma **casa**.

- O **Socket** é como a **porta** dessa casa.

Quando um processo quer enviar uma mensagem para outro computador, ele empurra a mensagem para fora da porta (o socket). Do outro lado da porta, existe uma infraestrutura de transporte (a rua/correios) que se encarrega de levar a mensagem até a porta (socket) do destino. O processo de destino, então, recebe a mensagem assim que ela passa por sua própria porta.

### O Papel do Socket na Arquitetura

O socket é a interface de programação de aplicativos (API) entre a **Camada de Aplicação** e a **Camada de Transporte**.

- **Controle do Desenvolvedor:** Da porta para dentro (Camada de Aplicação), o desenvolvedor tem controle total sobre o código, o formato das mensagens e as regras do protocolo.
- **Controle do Sistema Operacional:** Da porta para fora (Camada de Transporte/Rede), o controle é quase total do sistema operacional. O desenvolvedor da aplicação só consegue escolher qual protocolo de transporte usar (como TCP ou UDP) e configurar alguns poucos parâmetros, como o tamanho máximo dos buffers.

Para que a comunicação funcione, cada socket precisa ser identificado por um endereço único na rede, composto pelo **Endereço IP** (que identifica a máquina) e o **Número de Porta** (que identifica o processo específico dentro daquela máquina).