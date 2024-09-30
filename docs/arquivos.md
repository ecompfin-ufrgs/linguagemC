# Manipulação de arquivos

Como dito anteriormente, a linguagem C foi criada para escrever o sistema operacional Unix.  Por isso, os conceitos nela em muito
são reflexo dos conceitos do Unix.  Em particular, em Unix, todas as partes do sistema computacional são tratadas como arquivo,
isto é, todos os dispositivos de entrada, saída, memória secundária e até mesmo a rede são entendidos pelo sistema como arquivos,
ou, em linguajar mais preciso, *streams*.

Sendo assim, as funções existentes na biblioteca padrão para leitura e escrita de arquivos também estão contidas no cabeçalho 
<stdio.h>.
