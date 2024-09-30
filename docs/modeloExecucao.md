# Semântica de execução

A execução do programa se inicia pela função *main* e depois é realizada
sequencialmente ou por chamadas a outras funções que podem ou não serem
executadas em paralelo ou concorrentemente.[^1]

O código é executado de cima para baixo e da esquerda para direita.  Respeita-se
a ordem de operações aritméticas bem como o uso dos parênteses para dar prioridade
à operação.

Quando uma função é chamada, a função que a chamou é interrompida até o fim da execução da função chamada que, após terminar sua execução, devolve o controle a função que a chamou.

[^1]: Deixaremos os detalhes referentes à execução paralela e concorrente para 
tratamentos posteriores.
