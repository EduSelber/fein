Floyd-Washall
======
Objetivo do código 
---------

Este algoritimo tem o objetivo de encontrar todos os caminhos mais curtos entre os  vértices de um grafo 

![](Grafo-Desprog.png)

Este é um exemplo de grafo, esses grandes circulos são os vértices e as setas que ligam eles são as arestas. Os números em cima das arestas representam os pesos, ou seja, o quanto custa de deslocar de um vértice para o outro. 
Você pode estar se perguntando "Para que esse algorítmo serve, afinal?". Bem, se observar mais atentamente a figura, notará que nem todos os vértices desse grafo tem uma ligação direta entre eles. Seria impossível então se deslocar do vértice 1 até o 3? E se possível, qual o melhor "caminho" entre eles? 

Pois bem, todas essas perguntas também são feitas quando estamos pensando em nos locomover de um ponto a outro da cidade. E, ao abrir o Google Maps, somos respondidos! Ele e outros softwares se utilizam do algoritmo de Floyd-Warshall para solucionar esses problemas. Devidamente motivados, vamos pensar mais no código em si.

Exercício 1
-----------
(Este exercício será sobre preencher matriz)



Simulando o codigo
---------


??? Atividade

No codigo é necessário criar *n* vértices auxiliar, como isso é feito.
::: Gabarito

Para fazer isso o código faz um loop de  *n* interações, que a cada interação cria um vértice auxiliar

:::

???

??? Atividade

Após criar o vértice auxiliar como faz para testar ele e verificar se com ele encontra um caminho mais curto usando ele.
::: Gabarito

Para fazer isso é necessário dois loops para percorrer a matriz e a cada interação verificar se usando o vértice auxiliar  o custo é melhorado, caso sim ele atualiza o valor na matriz para o do vértice auxiliar.
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





