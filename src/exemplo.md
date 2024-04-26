Floyd-Washall
======

Subtítulo
---------

Para criar um parágrafo, basta escrever um texto contínuo, sem pular linhas.

Você também pode criar

1. listas;

2. ordenadas,

assim como

* listas;

* não-ordenadas

e imagens. Lembre que todas as imagens devem estar em uma subpasta *img*.

![](logo.png)

Para tabelas, usa-se a [notação do
MultiMarkdown](https://fletcher.github.io/MultiMarkdown-6/syntax/tables.html),
que é muito flexível. Vale a pena abrir esse link para saber todas as
possibilidades.

| coluna a | coluna b |
|----------|----------|
| 1        | 2        |

Ao longo de um texto, você pode usar *itálico*, **negrito**, {red}(vermelho) e
[[tecla]]. Também pode usar uma equação LaTeX: $f(n) \leq g(n)$. Se for muito
grande, você pode isolá-la em um parágrafo.

$$\lim_{n \rightarrow \infty} \frac{f(n)}{g(n)} \leq 1$$

Para inserir uma animação, use `md :` seguido do nome de uma pasta onde as
imagens estão. Essa pasta também deve estar em *img*.

:bubble

Você também pode inserir código, inclusive especificando a linguagem.

Simulando o codigo
---------


??? Atividade

No codigo é necessário criar *n* vértices auxiliar, como fazer isso.
::: Gabarito

Para fazer isso o código faz um loop de  *n* interações, que a cada interação cria um vértice auxiliar

:::

???

??? Atividade

Após criar o vértice auxiliar como faz para testar ele e verificar se com ele encontra um caminho mais curto usando ele.
::: Gabarito

Para fazer isso é necessário dois loops para percorrer a matriz e a cada interação verificar se usando o vertíce auxiliar melhora o custo , caso sim ele atualiza o valor na matriz para este.
:::

???
Abaixo está o código de Floyd Washall , o qual contém 3 loops, que ajudarão a percorrer a matriz e encontrar os menores camninhos entre os vértices.

Aqui embaixo está o código de floyd washall 

``` py
def floyd_warshall(graph):
    num_vertices = graph.shape[0]
    dist = graph.copy()
    iteracao = 0
    for k in range(num_vertices):
        for i in range(num_vertices):
            for j in range(num_vertices):
                if dist[i][j] > dist[i][k] + dist[k][j]:
                    dist[i][j] = dist[i][k] + dist[k][j]
                plot_and_save_matrix(dist, iteracao, i, j)
                iteracao += 1

    return dist
```

É importante comenta que a primeira linha do código armazena em uma variável local a quantidade total de vértices no grafo, o que é crucial para definir o número de iterações que cada loop deve executar.


Acompanhe pela animação, o que acontece com a matriz depois de cada interação do algoritimo

:Simulacao

!!! Aviso
Para o exercício abaixo é recomendado fazer passo a passo ao invés de tentar achar a resposta direto.
!!!

??? Exercício

![](Matriz_incial.png)

Tente simular o que acontecerá com está matriz depois de cada interação do código.

::: Gabarito
![](Matriz_final.png)

As alterações nessa matriz ocorreram nos vértices que não estavam conectado como, por exemplo, o caminho entre o vértice *1* e o *3*, que antes estava com um custo muito elevado, mas agora tem um custo três uma vez que foi usado vértice 2 como auxiliar. 
:::

???

``` c
void f() {
    printf("hello world\n");
}
```

Se não especificar nenhuma, o código fica com colorização de terminal.

```
hello world
```


!!! Aviso
Este é um exemplo de aviso, entre `md !!!`.
!!!


??? Exercício

Este é um exemplo de exercício, entre `md ???`.

::: Gabarito
Este é um exemplo de gabarito, entre `md :::`.
:::

???
