
---
Acontece quando a taxa de chegada de dados e maior que a velocidade que ele consegue processar e enviar adiante. 

Funcionamento no [[roteador]]:
1. Os pacotes chegam pelas portas de entrada do roteador
2. Se o link de saída já estiver ocupado transmitindo outro pacote, os novos pacotes que chegam não podem ser enviados imediatamente 
3. Eles são guardados no [[buffer]], esperando a sua vez de serem transmitidos. O tempo que o pacote passa ali parado esperando é o **atraso de fila**

