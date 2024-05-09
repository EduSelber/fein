Floyd-Washall
======
Objetivo do código 
---------

Este algoritimo tem o objetivo de encontrar todos os caminhos mais curtos entre os  vértices de um grafo 

![](Grafo-Desprog.png)

Este é um exemplo de grafo, esses grandes círculos são os vértices e as setas que ligam eles são as arestas. Os números em cima das arestas representam os pesos, ou seja, o quanto "custa" se deslocar de um vértice para o outro. 
Você pode estar se perguntando "Para que esse algorítmo serve, afinal?". Bem, se observar mais atentamente a figura, notará que nem todos os vértices desse grafo tem uma ligação direta entre eles. Seria impossível então se deslocar do vértice 1 até o 3? E se possível, qual o melhor "caminho" entre eles? 

Pois bem, todas essas perguntas também são feitas quando estamos pensando em nos locomover de um ponto a outro da cidade. E, ao abrir o Google Maps, somos respondidos! Ele e outros softwares se utilizam do algoritmo de Floyd-Warshall para solucionar esses problemas. Devidamente motivados, vamos pensar mais no código em si.

Quando se deve usar o algoritmo de Floyd-Warshall?
-------------------------------------------------
O algoritmo é uma excelente escolha em situações específicas, como quando é necessário calcular o caminho mais curto entre todos os pares de nós em um grafo ponderado, ou seja em cenários que se exige calcular todas as distâncias de pares de vértices.



Exercício 1
-----------




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

É importante comentar que a primeira linha do código armazena em uma variável local a quantidade total de vértices no grafo, o que é crucial para definir o número de iterações que cada loop deve executar.


Acompanhe pela animação, o que acontece com a matriz depois de cada interação do algoritimo

:Simulacao

!!! Aviso
Para o exercício abaixo é recomendado fazer passo a passo ao invés de tentar achar a resposta direto.
!!!

??? Exercício

![](Matriz_incial.png)

Tente simular o que acontecerá com está matriz depois de cada iteração do código.

::: Gabarito
![](Matriz_final.png)

As alterações nessa matriz ocorreram nos vértices que não estavam conectado como, por exemplo, o caminho entre o vértice *1* e o *3*, que antes estava com um custo muito elevado, mas agora tem um custo três uma vez que foi usado vértice 2 como auxiliar. 
:::

???



Aplicações práticas em que o algoritmo deve ser usado
-----------------------------------------------------
Pense em um contexto de redes de transporte, em uma cidade com várias estações de ônibus ou metrô, cada uma conectada diferentes e diversas rotas específicas. O objetivo é determinar o tempo de viagem mais curto entre todas as estações, considerando todas as possíveis conexões diretas e indiretas.

Imagine uma cidade com 5 estações de ônibus, de A até E, com as seguintes conexões, diretas e indiretas, e pesos(tempos/distância). 
Você foi designado a trabalhar na otimização dessa rede.

 * A conecta com B em 4 minutos.
 * A conecta com D em 10 minutos.
 * B conecta com C em 5 minutos.
 * C conecta com B em 5 minutos.
 * D conecta com E em 15 minutos.
 * E conecta com B em 10 minutos.
 * C conecta com E em 7 minutos.


??? Exercício: Modelando o problema
    1. Pense, quem será a rodoviária e o que o tempo representa no problema.
::: Gabarito
    * Cada estação será um vértice no grafo;
    * Cada rota direta entre duas estações será uma aresta no grafo,  com peso correspondente ao tempo de viagem entre essas duas estações.

    :::

??? Exercício: Implementando o algoritmo
    2. Agora você vai implementar o algoritmo. Aplique a situação descrita na matriz inicial, nesse caso baseando nos tempos de viagem diretos entre as estações e se não houver conexão direta, o valor passa a ser infinito. Desenhe o grafo e depois implemente o algoritmo para obter o resultado de todos os pares da tabela.

::: Gabarito
``` c
void floydWarshall() {
int dist[V][V], i, j, k;

    // Inicializa a matriz de solução da mesma forma que a matriz de entrada do grafo
    for (i = 0; i < V; i++)
        for (j = 0; j < V; j++)
            dist[i][j] = graph[i][j];
 // Adiciona todos os vértices um por um ao conjunto de vértices intermediários.     
    for (k = 0; k < V; k++) {
        // vértices como fonte
        for (i = 0; i < V; i++) {
            // vértices como destino para a fonte escolhida
            for (j = 0; j < V; j++) {

                if (dist[i][k] + dist[k][j] < dist[i][j])
                    dist[i][j] = dist[i][k] + dist[k][j];
            }
        }
    }
}
``` 
:::
No final, você terá uma matriz de distâncias que fornecerá o tempo de viagem mais curto entre cada estação rodoviária.

Complexidade do Algoritmo
--------------------------
Agora nós já podemos supor como será a complexidade do algoritmo. 

:::Gabarito
O algoritmo tem uma complexidade de O(n^3) . Lembre-se para cada dois vértices, existe uma iteração intermediária.
:::

Eficiência do Algoritmo
------------------------
E a eficiência do algoritmo?
:::Gabarito
A eficiência de memória será O(n^2), já que salvamos a matriz em uma última iteração e suas dimensões são n x n.
:::





