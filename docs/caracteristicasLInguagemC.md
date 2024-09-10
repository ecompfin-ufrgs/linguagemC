# Características da linguagem: código-fonte, escopo, gestão de memória e implementações
C é uma linguagem de programação que dá suporte exclusivamente ao paradigma procedural.  Por isso, seu código-fonte deve estar inserido dentro de funções ou procedimentos, admitindo-se como exceção apenas a parte inicial do código que será usada para inserção de códigos proveniente de bibliotecas externas ou para definições de valores previamente ao início da execução do programa.   Entre todas as funções ou procedimentos do código-fonte C, destaca-se a função que dá início à execução do programa e orienta a execução de todo o programa, que é chamada de função principal.  

O código-fonte de um programa escrito em C deve ser inserido em um arquivo de texto do sistema operacional onde o programa é escrito com extensão .C .  Por exemplo, um programa com nome "hello" teria o arquivo de código-fonte nomeado "hello.c".  Este código-fonte é dividido em trechos denominados de trecho de escopo global e trecho de escopo local. O trecho de escopo global é a primeira parte do código-fonte e manipula os objetos da linguagem que serão armazenados em memória durante todo o tempo de execução do programa, sendo incluído fora de qualquer função e anteriormente à definição da função principal ao passo que o trecho de escopo local está inserido dentro de funções e contém objetos que durarão apenas enquanto o trecho de código desta função estiver sendo executado.

Os trechos do código-fonte estão associados univocamente a regiões de memória alocadas (medida em termos de bytes) pelo sistema operacional como uma estrutura de dados pilha (pense numa pilha de pratos) quando da execução do programa.  Esta pilha de bytes de memória está organizada de baixo para cima em cinco grandes segmentos: text, initialized data, uninitialized data, heap e stack.  Ou seja, o text é o "prato" mais no fundo da pilha e o stack é o prato mais no topo.

O segmento text armazena o próprio executável do programa. O segmento initialized data guarda os dados inicializados pelo programador no escopo global ou como estáticos, isto é, dados com valores fixados antes da execução e que não mudarão de valor durante toda a execução do programa.  Já o uninitialized data é uma área reservada a dados não inicializados pelo programador.  O heap é o segmento de memória que será alocado durante a execução do programa (alocação dinâmica de memória) e o stack guarda os dados que estão armazenados no trecho de escopo local do código-fonte.

A gestão de memória é manual, cabendo ao programador garantir que os dados que serão lidos caibam dentro da quantidade de memória alocada para eles pelo sistema.  Por isso, cada tipo de dado tem uma quantidade de dados pré-determinada.  Caso um dado ultrapasse a quantidade de memória disponível para ele será gerado um tipo de erro inesperado conhecido como "undefined behavior", que é um erro catastrófico no programa.  Um tipo de erro que provoca undefined behavior é o famigerado "stack overflow", que ocorre quando a quantidade de dados colocada no stack é maior do que caberia nele.

Quanto às implementações da linguagem C, elas existem para praticamente qualquer plataforma de computação desde os menores microcontroladores até os grandes supercomputadores.  Há inclusive implementações que emitem código para executáveis que rodam diretamente no hardware sem a necessidade de um sistema operacional! Normalmente, a implementação de C é feita por meio de um compilador, porque originalmente a linguagem foi criada para desenvolvimento do sistema operacional Unix, mas existem interpretadores experimentais para C. Aqui utilizaremos para exemplificar nossos códigos o compilador C fornecido pelo Projeto GNU que é conhecido com GCC. 

# Objetos e tipos de dados em C

Os dados manipulados por programas escritos em C são armazenados em segmentos de memória denominados objetos que contém 1 ou mais bytes, ou seja, C é capaz de endereçar bytes de memória, mas não bits.  Ainda assim, existes "hacks", que estão além do escopo destas notas, para se endereçar bits em caso necessário.

O tamanho de cada objeto depende do tipo de dado armazenado.  Note-se que tipo de dado é, por definição, o conjunto ao qual pertece o dado armazenado acompanhado das operações que podem ser realizadas com dados deste conjunto.  C oferece os seguintes tipos de dados primitivos 

<table>
<tr>
<td>Tipo de dado </td>
<td> Sintaxe </td>
<td>Tamanho do objeto (em bytes)</td>
</tr>
  <tr><td>Caracter</td><td>char</td><td>1</td></tr>
  <tr><td>Inteiro</td><td>Inteiro</td><td>4</td></tr>
<\table>
  
 [fonte](https://byjus.com/gate/size-of-data-types-in-c/#size-of-primary-data-types)



# Definição formal
A linguagem é definida como formada por:

1. elementos preliminares;
2. ambientes de tradução e execução;
3. sintaxe, 
4. bibliotecas.

O [Padrão C](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2310.pdf)
apresenta a definição formal da linguagem, mas baseia-se no
[Manual de Referência](https://www.bell-labs.com/usr/dmr/www/cman.pdf)
escrito originalmente pelo criador da linguagem Dennis Ritchie.

## Elementos léxicos

O texto do programa C é armazenado em arquivos denominados arquivos-fontes
contendo preferencialmente por caracteres ASCII, embora haja
suporte para caracteres UTF-8 no padrão mais recente para os sistemas
operacionais de computadores pessoais.

Os arquivos-fonte terão a extensão *.C* e os arquivos cabeçalhos terão extensão *.h*.

Os seguintes duplas de caracteres, denominadas sequências de escape estão
disponíveis para controlar o local de impressão dos caracteres:

- \a -> produz um som
- \b -> backspace
- \f -> move o cursor para o início da próxima página
- \n -> move o cursor para o início da próxima linha
- \r -> move o cursor para o início da linha atual
- \t -> move o cursor para a próxima tabulação horizontal
- \v -> move o cursor para a próxima tabulação vertical.

Identificadores são sequências de caracteres usados para nomear variáveis,
funções e tipos de dados criados pelo programador.  Cada linha deve ser
terminada pelo *;*.

## Estrutura do programa
Além dos arquivos-fontes o código-fonte C fica armazenado em arquivos-cabeçalhos
(headers) que orientam o processo de tradução do arquivo-fonte para formato
binário.  Os *headers* são adicionados aos arquivos-fontes usando o comando
(ou diretiva de tradução) #include.  Arquivos-fontes e headers são denominados
em conjunto como  unidades de pré-processamento de tradução.[^1]

Entre os arquivos-fontes, um deles deverá conter uma função denominada *main*
com retorno inteiro igual a zero definida como segue:
```c
int main(void){

/* comandos */

}
```
Preferivelmente, porém, a função *main* pode ser definida desta outra forma:

```c
int main(int argc, char *argv[]){
/*comandos*/
}
```
Neste caso, o parâmetro argc deve ser não negativo e que representa o número 
de parâmetros que o programa recebe no terminal e o parâmetro argv consiste
na relação de parâmetros que a função receberá.

Como todo o código-fonte fica localizado dentro de uma função, diz-se que C
é uma linguagem procedural.

A linguagem C não possui no seu núcleo capacidade de realizar entrada/saída de
dados, relegando tal funcionalidade a bibliotecas a fim de poder ser 
facilmente portada.

## Fases da tradução
Simplificadamente, a tradução é feita como segue:

1. O arquivo-fonte é mapeado em sequências de caracteres;
2. Comentários são apagados;
3. As diretivas de pré-processamento dos headers são executadas e apagadas;
4. Elementos das bibliotecas são ligados ao programa, e
5. É gerado o código executável do programa.


[^1]: Na prática, as principais implementações da linguagem C são todas
compiladores e, portanto, tomaremos a liberdade de usar a palavra
compilação livremente como sinônimo de tradução.

