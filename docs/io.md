# Operações de entrada e saída de dados

C não dispõe de funções de entrada e saída, relegando estas operações para
bibliotecas específicas.  De qualquer forma, C oferece na sua
[biblioteca-padrão](https://www.gnu.org/software/libc/manual/pdf/libc.pdf) funções
para realização de entrada e saída de baixo nível (*file descriptors*) ou alto nível (*streams*). Aqui trataremos apenas
das funções de alto nível, posto que esta introdução não se destina a programação
de sistemas.

*Streams* são a forma como arquivos são armazenados e tratados por C, sendo, de fato, estruturas de dados em memória conectadas aos os arquivos, servindo como
seus representantes.  Note que C trata como arquivo tanto os dispositivos do sistema (como teclado, monitor, mouse, etc) quanto processos sendo executados, inclusive os referentes a dispositivos de rede ou ainda arquivos em disco.

O arquivo de cabeçalho <stdio.h> da biblioteca-padrão oferece as funções de alto nível para tratar streams bem como, no início da execução função main, proporciona automaticamente três streams:

- FILE * stdin
- FILE * stdout
- FILE * stderr

Estes arquivos (streams) referem-se respectivamente aos dispositivos padrão de entrada, saída e a um arquivo onde se armazenam os erros.

Os detalhes das operações com as funções do arquivo cabeçalho stdio.h serão vistos na prática, deixando a descrição para a referência da biblioteca disponível [aqui](https://www.gnu.org/software/libc/manual/pdf/libc.pdf) 

- 
