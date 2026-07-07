- **Definição:** É uma área de memória interna presente nos comutadores (como roteadores e switches) associada a cada uma de suas interfaces de saída.
    
- **Papel no Tráfego:** Funciona como um reservatório temporário. Quando pacotes chegam de várias linhas de entrada ao mesmo tempo e precisam sair todos pela mesma linha de saída, eles não podem ser transmitidos em paralelo se a capacidade física do cabo não permitir. O roteador armazena esses pacotes excedentes no _buffer_ para que eles esperem a sua vez na fila.
    
- **Relação com Problemas:** É o acúmulo de pacotes no buffer que gera o **atraso de fila**. E quando essa memória enche completamente, o espaço esgota e ocorrem as perdas de dados (_buffer overflow_).