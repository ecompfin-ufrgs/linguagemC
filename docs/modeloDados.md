# Semântica dos dados

Os dados manipulados por programas escritos em C são armazenados em segmentos de memória denominados objetos que contém 1 ou mais bytes, ou seja, C é capaz de endereçar diretamente bytes de memória, mas não bits.  Ainda assim, existem "hacks", que estão além do escopo destas notas, para se endereçar bits em caso necessário.

O tamanho de cada objeto depende do tipo de dado armazenado.  Note-se que tipo de dado é, por definição, o conjunto ao qual pertece o dado armazenado acompanhado das operações que podem ser realizadas com dados deste conjunto.  C oferece os seguintes tipos de dados primitivos

Tipo de dado | Sintaxe |Tamanho do objeto (em bytes)|
_____________________________________________________
Caracter     |char     |              1             |
____________________________________________________|
Inteiro      |Inteiro  |              4             |
____________________________________________________|

[fonte](https://byjus.com/gate/size-of-data-types-in-c/#size-of-primary-data-types)
os bytes neles armazenados.

## Tipos primitivos

### Inteiros

- signed char
- unsigned char
- char
- short int
- int
- unsigned short int
- int
- unsigned int
- long int
- unsigned long int
- long long int
- unsigned long long int

### Reais

- float
- double
- long double

Em virtude de problemas de precisão números de ponto flutuante, não se deve
comparar números reais.

### Complexos

- float _Complex  ou float complex
- double _Complex ou double complex
- long double _Complex ou long double complex
