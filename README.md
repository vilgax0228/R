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
```R
> help(solve)
```

Para um recurso especificado por caracteres especiais, o argumento deve ser colocado entre aspas duplas ou simples, isso também é necessário para algumas palavras com significado sintático, incluindo *if*, *for* e *function*.
```R
> help("[[")
```

help está disponível em formato HTML executando:
```R
> help.start()
```

# Diretório
```R
> getwd()  # getwd: get working directory
```
Mostra onde está o seu diretório.
```R
> dir()
```
Mostra o que está no seu diretório.

## Entering Input
No prompt do R, digitamos expressões. O símbolo **<-** é o operador de atribuição.
```R
> x <- 1
> print(x)
[1] 1
> msg <- "hello"
```

A gramática da linguagem determina se uma expressão está completa ou não.
```R
> x <-  # incomplete expression
```
O caractere # indica um comentário. Qualquer coisa à direita do # (incluindo o próprio #) é ignorada.

## Evaluation
Quando uma expressão é inserida no prompt, ela é avaliada e o resultado da expressão é retornado. O resultado pode ser printado automaticamente ou não.
```R
> x <- 5    # nothing printed
> x         # auto-printing occurs
[1] 5
> print(x)  # explicit printing
[1] 5
```
O [1] mostrado no output indica que x é um **vetor** e 5 é o seu primeiro elemento.

Quando um vetor no R é printado você irá notar que um *index* para o vetor é printado em parêntesis [] ao lado.

Por exemplo, essa sequência de inteiros de tamanho (*length*) 20:
```R
> x <- 10:30
> x
[1] 10 11 12 13 14 15 16 17
[9] 18 19 20 21 22 23 24 25
[17] 26 27 28 29 30
```
Os números em parêntesis não fazem parte do vetor em si, eles são apenas parte do output printado.

* Observe que o operador **:** é usado para criar uma sequência de inteiros.

## R Objects
R têm 5 classes básicas ou "atômicas" de objetos.
* caracteres (chr)
* numérico (números reais) (num)
* inteiro (int)
* complexo (cplx)
* lógico (TRUE/FALSE)

*O tipo mais básico de um objeto no R é um vetor.*

Vetores vazios podem ser criados com a função *vector()*.

Um vetor só pode conter objetos de mesma classe. Mas há uma excessão, que é uma lista (*list*).  
Uma lista é representada como um vetor mas pode conter objetos de diferentes classes. De fato, geralmente é esse o motivo de usarmos elas.

## Números
Números no R são usualmente tratados como objetos numéricos (números reais com precisão de duas casas decimais).  

Isso significa que mesmo quando você se depara com um número como "1" ou "2" no R, que talvez te leve a pensar como sendo um inteiro, eles são normalmente representados por detrás das cortinas como objetos numéricos (algo como "1.00" ou "2.00").  

Se você quer um inteiro explicitamente, precisa especificar o sufixo *L*.

Então digitando 1 no R gera um objeto numérico;  
Digitando 1L explicitamente gera um objeto de inteiro.

Existe também um número especial *Inf* que representa infinito.

Isso nos permite representar entidades como 1/0. Dessa maneira, Inf pode ser usado em cálculos habituais; 1/Inf é 0.

O valor **NaN** representa um valor indefinido ("not a number"); 0/0.  
NaN pode ser pensado também como um valor que está ausente.

## Atributos
Objetos no R podem ter atributos, que são como metadados do objeto. Eles ajudam a descrever o objeto.

Por exemplo, nomes de colunas em um *data frame* nos ajuda a dizer que tipo de dado está armazenado em cada uma das colunas.

Alguns exemplos de atributos de objetos no R são:
* names, dimnames
* dimensions (ex. matrices, arrays)
* class (ex. integer, numeric)
* length

atributos de um objeto podem ser acessados usando a função *attributes()*.

## Criando vetores
A função **c()** pode ser usada para criar vetores de objetos concatenando coisas juntas.
```R
> x <- c(0.5, 0.6)       # numeric
> x <- c(TRUE, FALSE)    # logical
> x <- c(T, F)           # logical
> x <- c("a", "b", "c")  # character
> x <- 9:29              # integer
> x <- c(1+0i, 2+4i)     # complex
```

Você também pode usar a função **vector()** para criar vetores.
```R
> x <- vector("numeric", length=10)
> x
[1] 0 0 0 0 0 0 0 0 0 0
```

## Objetos ausentes
existem ocasiões aonde classes diferentes de objetos no R ficam misturadas.
```R
> y <- c(1.7, "a")   # character
> y <- c(TRUE, 2)    # numeric
> y <- c("a", TRUE)  # character
```

Em cada caso acima, nós estamos misturando objetos de duas classes diferentes em um vetor.  
Mas lembre-se de que a única regra sobre vetores diz que isso não é permitido.

Quando objetos diferentes são misturados em um vetor, *coercion* (ou conversão) acontece para que cada elemento dentro do vetor seja da mesma classe.

No exemplo acima, vemos o efeito da coerção implícita.

O que o R tenta fazer é encontrar uma maneira de representar todos os objetos no vetor de forma razoável.  
Vão ter vezes em que isso faz exatamente o que você queria e... às vezes não.

Por exemplo, ao combinar um objeto numérico com um objeto de caractere isso irá criar um vetor de caractere, já que números podem ser mais facilmente representados como strings.

## Conversão explícita
Objetos podem ser explicitamente convertidos de uma classe para outra usando a função **as.**, se possível.
```R
> x <- 0:6
> class(x)
[1] "integer"
> as.numeric(x)
[1] 0 1 2 3 4 5 6
> as.logical(x)
FALSE TRUE TRUE TRUE TRUE TRUE TRUE
> as.character(x)
[1] "0" "1" "2" "3" "4" "5" "6"
```

Pode acontecer do R não conseguir desvendar como converter um objeto e isso pode resultar em *NAs* sendo produzidos.
```R
> x <- c("a", "b", "c")
> as.numeric(x)
Warning: NAs introduced by coercion
[1] NA NA NA
> as.logical(x)
[1] NA NA NA
> as.complex(x)
[1] NA NA NA
```

## Matrizes
Matrizes são vetores com um atributo de **dimensão**. O atributo de dimensão é ele próprio um vetor de inteiros de comprimento 2 (número de linhas, número de colunas).
```R
> m <- matrix(nrow=2, ncol=3)
> m
      [,1] [,2] [,3]
[1,]    NA   NA   NA
[2,]    NA   NA   NA
> dim(m)
[1] 2 3
> attributes(m)
$dim
[1] 2 3
```
Matrizes são construídas em relação à coluna, então as entradas podem ser pensadas como começando do canto superior esquerdo e correndo para baixo na coluna.
```R
> m <- matrix(1:6, nrow=2, ncol=3)
> m
      [,1] [,2] [,3]
[1,]     1    3    5
[2,]     2    4    6
```
Matrizes também podem ser criadas diretamente através de vetores adicionando um atributo de dimensão.
```R
> m <- 1:10
> m
[1] 1 2 3 4 5 6 7 8 9 10
> dim(m)
NULL
> dim(m) <- c(2, 5)
> m
      [,1] [,2] [,3] [,4] [,5]
[1,]     1    3    5    7    9
[2,]     2    4    6    8   10
```
Matrizes podem ser criadas por meio da união de colunas ou da união de linhas com as funções **cbind()** e **rbind()**.
```R
> x <- 1:3
> y <- 10:12
> cbind(x, y)
      [,1] [,2]
[1,]     1   10
[2,]     2   11
[3,]     3   12
> rbind(x, y)
      [,1] [,2] [,3]
[1,]     1    2    3
[2,]    10   11   12
```

## Listas
