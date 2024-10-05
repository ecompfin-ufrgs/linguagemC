# Características da linguagem

## Código-fonte e escopo

A linguagem C foi criada na década de 1970 para implementar o sistema operacional UNIX. Por esse motivo, seus criadores a fizeram tão simples que sequer conta com mecanismos de entrada e saída de dados em sua especificação, deixando isso para sua biblioteca-padrão o que facilita a implementação em diversos ambientes, desde dispositivos embarcados até supercomputadores, passando, naturalmente, por computadores pessoais. Esta facilidade de implementação propiciou ao surgimento de diversos compiladores capazes de produzir código-objeto altamente otimizado e, consequentemente, a linguagem passou a ser muito usada quando se necessita de programas ou bibliotecas de código de alto desempenho.

Nesse mesmo sentido de simplicidade e facilidade, C é uma linguagem de programação que dá suporte exclusivamente ao paradigma procedural, devendo a integralidade do código-fonte de seus programas estar incluída dentro de funções armazenadas em um arquivo de texto do sistema operacional com extensão .c.  Este arquivo pode incluir também instruções dirigidas ao tradutor sobre a forma como deve ser feita a tradução.  Como normalmente o tradutor de um arquivo fonte c é um compilador tais instruções são costumeiramente denominadas diretivas de compilação.

As diretivas de compilação, por serem processadas pelo compilador e, por isso, antes da execução do programa, são também conhecidas como diretivas de pré-processamento. Entre as diretivas de pré-processameto, há instruções para a inclusão de bibliotecas, definição de variáveis globais, instruções para substituição de caracteres identificadores de variáveis nos arquivos de programa por valores pré-definidos (instruções chamdas **macros**) e instruções para a inclusão de funções definidas em arquivos de programa. Estas diretivas podem também estar inseridas em arquivos específicos com extensão .h para melhorar a modularização do programa e também para acelerar a execução dos mesmos, transferindo trabalho de tempo de execução para tempo de compilação.

Todo o conteúdo externo às funções dos arquivos de programa (.c) considera-se parte do trecho de escopo global, pois manipula objetos que serão armazenados em memória durante todo o tempo de execução do programa.  Já o restante do código-fonte - chamado trecho de *escopo local* - contém objetos que durarão apenas enquanto o trecho de código desta função estiver sendo executado.  De fato, a boa prática de programação C reza que, no escopo global, deve haver apenas códigos provenientes de bibliotecas externas ou para definições de valores previamente ao início da execução do programa.   Entre todas as funções ou procedimentos do código-fonte C, destaca-se a função que é o ponto de entrada da execução do programa e orienta a execução de todo o programa, que é chamada de função principal.

## Gestão de memória

Os trechos do código-fonte estão associados univocamente a regiões de memória alocadas pelo sistema operacional como uma estrutura de dados pilha (pense numa pilha de pratos) quando da execução do programa.  Esta pilha de memória cuja dimensão é medida em bytes está organizada de baixo para cima em cinco grandes segmentos: text, initialized data, uninitialized data, heap e stack.  Ou seja, o text é o "prato" mais no fundo da pilha e o stack é o prato mais no topo.

O segmento text armazena o próprio executável do programa. O segmento initialized data guarda os dados inicializados pelo programador no escopo global ou como estáticos, isto é, dados com valores fixados antes da execução e que não mudarão de valor durante toda a execução do programa.  Já o uninitialized data é uma área reservada a dados não inicializados pelo programador.  O heap é o segmento de memória que será alocado durante a execução do programa (alocação dinâmica de memória) e o stack guarda os dados que estão armazenados no trecho de escopo local do código-fonte.

Os dados armazenados na memória possuem tipos, isto é, pertencem a um conjunto de valores em relação aos quais estão definidas as operações que podem ser realizadas com eles, usando a linguagem.  Deste modo, a cada endereço de
memória fica associado um tipo.  Cada tipo de dado ocupa uma quantidade de memória previstas na [especificação da linguagem](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n1256.pdf).

A gestão de memória é manual, cabendo ao programador garantir que os dados que serão lidos caibam dentro da quantidade de memória alocada para eles pelo sistema de acordo com o tipo especificado pelo programador.  Não obstante, a depender do segmento da memória, esta gestão deve ser acompanhada mais ou menos de perto.  Assim, o limite de tamanho do text segment é determinado pela quantidadede memória física do sistema computacional.  O initialized data está limitado apenas pelo tamanho do tipo de dado tal como o unitialized data.  O heap e o stack é que devem ser tratados com especial atenção pelos programadores, porque eles crescem em direção contrária na pilha de memória alocada ao programa pelo sistema operacional.  Mais particularmente ainda deve-se atentar para o heap, porque seu crescimento é determinado durante o tempo de execução do programa (e não no momento da escrita - chamado de tempo de compilação).  Há instruções específicas em C para permitir ao programador controlar o heap de modo a evitar que ele cresça indefinidamente e avance sobre o stack.

Caso um dado ultrapasse a quantidade de memória disponível para ele será gerado um tipo de erro inesperado conhecido como [undefined behavior](https://en.wikipedia.org/wiki/Undefined_behavior), que é um erro catastrófico no programa.  Um exemplo de erro que provoca undefined behavior é o mencionado **stack overflow**, que ocorre quando a quantidade de dados colocada no stack é maior do que caberia nele ou se o heap cresceu sobre o stack.

## Implementações

Quanto às implementações da linguagem C, elas existem para praticamente qualquer plataforma de computação desde os menores microcontroladores até os grandes supercomputadores.  Há inclusive implementações que emitem código para executáveis que rodam diretamente no hardware sem a necessidade de um sistema operacional! Normalmente, a implementação de C é feita por meio de um compilador, porque originalmente a linguagem foi criada para desenvolvimento do sistema operacional Unix, mas existem interpretadores experimentais para C. Aqui utilizaremos para exemplificar nossos códigos o compilador C fornecido pelo Projeto GNU que é conhecido com GCC.

O [Padrão C](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n1256.pdf)
apresenta a definição formal da linguagem, mas baseia-se no
[Manual de Referência](https://www.bell-labs.com/usr/dmr/www/cman.pdf)
escrito originalmente pelo criador da linguagem Dennis Ritchie.

## Estrutura do programa

Além dos arquivos-fontes o código-fonte C fica armazenado em arquivos-cabeçalhos
(headers) que orientam o processo de tradução do arquivo-fonte para formato
binário.  Os *headers* são adicionados aos arquivos-fontes usando o comando
(ou diretiva de tradução) #include.  Arquivos-fontes e headers são denominados
em conjunto como  unidades de pré-processamento de tradução.[^1]

Entre os arquivos-fontes, um deles deverá conter uma função denominada *main*
com retorno inteiro igual a zero definida como segue:

```c
#include <stdio.h>

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
