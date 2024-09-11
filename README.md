**R** é um conjunto integrado de ferramentas de software para manipulação de dados, cálculos e visualização gráfica.

Um ambiente no qual muitas técnicas estatísticas clássicas e modernas foram implementadas. Algumas dessas técnicas estão incorporadas no ambiente base do R, mas muitas são fornecidas como pacotes.

O sistema base do R contém, entre outras coisas, o pacote base, que é necessário para executar o R e contém as funções mais fundamentais.

Os outros pacotes contidos no sistema base incluem *utils, stats, datasets, graphics, grDevices, grid, methods, tools, parallel, compiler, splines, tcltk, stats4*.

Há também pacotes recomendados: *boot, class, cluster, codetools, foreign, KernSmooth, lattice, mgcv, nlme, rpart, survival, MASS, spatial, nnet, Matrix*.

Em Stages in the Evolution of *S*, John Chambers escreve que eles queriam desenvolver uma linguagem que pudesse atender facilmente tanto usuários quanto desenvolvedores. Mais tecnicamente, eles precisavam criar uma linguagem que fosse adequada tanto para a análise de dados interativa (mais baseada em linha de comando) quanto para escrever programas mais longos (mais semelhante a uma linguagem de programação tradicional).

# Recursos
[*documentação oficial*](https://cran.r-project.org/doc/manuals/r-release/R-intro.html)  
[*R Data Import/Export*](https://cran.r-project.org/doc/manuals/r-release/R-data.html)  
*R Programming for Data Science*

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
Quando uma expressão é inserida no prompt, ela é avaliada e o resultado da expressão é retornado. O resultado pode ser printado automaticamente ou não.
```
x <- 5  # nothing printed
x  # auto-printing occurs
[1] 5
print(x)  # explicit printing
[1] 5
```
* O [1] mostrado no output indica que x é um **vetor** e 5 é o seu primeiro elemento.  
Quando um vetor no R é printado você irá notar que um *index* para o vetor é printado em parêntesis [] ao lado.  
Por exemplo, essa sequência de inteiros de tamanho (*length*) 20:
```
x <- 10:30
x
[1] 10 11 12 13 14 15 16 17
[9] 18 19 20 21 22 23 24 25
[17] 26 27 28 29 30
```
Os números em parêntesis não fazem parte do vetor em si, eles são apenas parte do output printado.
* Observe que o operador **:** é usado para criar uma sequência de inteiros.

# R Objects
R têm 5 classes básicas ou "atômicas" de objetos.
* caracteres  # character (chr)
* numérico (números reais)  # numeric (num)
* inteiro  # integer (int)
* complexo  # complex (cplx)
* lógico  # logical (TRUE/FALSE)

*O tipo mais básico de um objeto no R é um vetor.*  
Vetores vazios podem ser criados com a função *vector()*.
Um vetor só pode conter objetos de mesma classe. Mas há uma excessão, que é uma lista (*list*).  
Uma lista é representada como um vetor mas pode conter objetos de diferentes classes. De fato, geralmente é esse o motivo de usarmos elas.

# Números
Números no R são usualmente tratados como objetos numéricos (números reais com precisão de duas casas decimais).  
