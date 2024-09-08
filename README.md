**R** é um conjunto integrado de ferramentas de software para manipulação de dados, cálculos e visualização gráfica.

Um ambiente no qual muitas técnicas estatísticas clássicas e modernas foram implementadas. Algumas dessas técnicas estão incorporadas no ambiente base do R, mas muitas são fornecidas como pacotes.

O sistema base do R contém, entre outras coisas, o pacote base, que é necessário para executar o R e contém as funções mais fundamentais.

Os outros pacotes contidos no sistema base incluem *utils, stats, datasets, graphics, grDevices, grid, methods, tools, parallel, compiler, splines, tcltk, stats4*.

Há também pacotes recomendados: *boot, class, cluster, codetools, foreign, KernSmooth, lattice, mgcv, nlme, rpart, survival, MASS, spatial, nnet, Matrix*.

Em Stages in the Evolution of *S*, John Chambers escreve que eles queriam desenvolver uma linguagem que pudesse atender facilmente tanto usuários quanto desenvolvedores. Mais tecnicamente, eles precisavam criar uma linguagem que fosse adequada tanto para a análise de dados interativa (mais baseada em linha de comando) quanto para escrever programas mais longos (mais semelhante a uma linguagem de programação tradicional).

# Buscando ajuda com funções e features
Para obter mais informações sobre qualquer função específica, por exemplo, *solve*, o comando é:
```
help(solve)
```

Para um recurso especificado por caracteres especiais, o argumento deve ser colocado entre aspas duplas ou simples, isso também é necessário para algumas palavras com significado sintático, incluindo *if*, *for* e *function*.
```
help("[[")
```

help está disponível em formato HTML executando:
```
help.start()
```

# Diretório
```
getwd()  # getwd: get working directory
```
Mostra onde está o seu diretório.
```
dir()
```
Mostra o que está no seu diretório.

# Entering Input
No prompt do R, digitamos expressões. O símbolo **<-** é o operador de atribuição.
```
x <- 1
print(x)
```
```
[1] 1
```

```
msg <- "hello"
```

A gramática da linguagem determina se uma expressão está completa ou não.
```
x <-  # incomplete expression
```
O caractere # indica um comentário. Qualquer coisa à direita do # (incluindo o próprio #) é ignorada.

# Evaluation
