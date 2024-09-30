# 2. Léxico básico

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

Além dos caracteres mencionados acima, também são especialmente importantes os que seguem:

Comentário de linha única - //

Comentário de múltiplas linhas - /* Isto é um comentário que pode ser estender
por múltiplas linhas */

Separadores de algarismos em números grandes: Exemplo: 1_000_000
