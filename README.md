# RACKETE E03
# Exercícios

Para a resolução dos exercícios será necessário baixar o código do repositório [[https://github.com/lvsreis/dcc019][DCC019]].
No repositório há instruções de como instalar e testar.

Todos os códigos dos exercícios encontram-se na pasta *exercise*

1. Altere a implementação da linguagem EREF de modo que a expressão da direita é avaliada
   antes da expressão da esquerda na operação na operação de diferença.
   Qual o valor do programa a seguir considerando essa nova especificação?

let g = let counter = newref(0)
        in proc(dummy)
            begin
             setref(counter, -(deref(counter), -(0,1)));
             deref(counter)
            end
in let a = (g 11)
   in let b = (g 11)
      in -(a,b)

2. A linguagem IREF é orientada a expressões: a principal categoria sintática de interesse é expressão
   e os programas computam valores das expressões.
   Baseado na linguagem IREF, implemente a linguagem IMP cuja principal categoria sintática é o comando, conforme a especificação abaixo:

   Prog → Stmt
   Stmt → ID = Expr
        | "print" Expr
        | "{" Stmt StmtList "}"
        | if Expr Stmt Stmt
        | while Expr Stmt
        | var ID ; Stmt
   Stmtlist → ; Stmt StmtList
        | ϵ

   Na especificação acima, o não-terminal Expr referencia as expressões de IREF.
   A semântica da atribuição (ID = Expr), condicional, impressão e bloco são como usual.
   A semântica do comando var ID ; Stmt define uma variável alocada implicitamente no estado
   cujo escopo é limitado ao comando subsequente.

   O código a ser modificado encontra-se na pasta /exercise/imp.
