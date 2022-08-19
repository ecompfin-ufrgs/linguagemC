# Características da linguagem

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

Os arquivos-fonte podem terão a extensão *.C* e os arquivos cabeçalhos terão extensão *.h*.

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
Ou alternativamente a função *main* pode ser definida desta outra forma:

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

