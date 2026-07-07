- **Definição:** É um dos protocolos centrais da internet, operando na camada de transporte. Ele trabalha diretamente acima do IP para fornecer uma entrega de dados confiável entre as aplicações que rodam nos sistemas finais.
    
- **Principais Funções:**
    
    - _Garantia de Entrega:_ Ao contrário do IP (que apenas tenta enviar o pacote, mas não garante que ele chegue), o TCP verifica se o dado foi recebido e o retransmite se houver perda.
        
    - _Controle de Fluxo e de Congestionamento:_ Ajusta a velocidade com que os dados são enviados para não sufocar o destinatário ou sobrecarregar os roteadores da rede.
        
- **Escopo:** Ele roda **estritamente nos sistemas finais (hosts)**. Os roteadores no núcleo da rede não processam o TCP; eles apenas repassam os pacotes IP que carregam os segmentos TCP dentro.