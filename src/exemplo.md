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


O que o código recebe 
---------
Os grafos são recurso visuais, que necessitam uma tradução para os códigos para ajudar ele a melhor entender este grafo.
??? Atividade

Qual é a melhor tradução para este código
::: Gabarito

A melhor forma do algoritimo de conseguir intepretar este grafo é através de uma matriz, em que as linhas e as colunas são os vértices  

:::
??? Atividade

Na matriz, o que significa o código ver a posícão linha 1 colouna 2?
::: Gabarito
Nessa posição o código verá o custo do caminho de sair do vértice 1 e ir até o vértice 2

:::
Simulando o codigo
---------

O algoritmo de Floyd-Warshall, como mencionado anteriormente, visa encontrar o caminho mais curto entre todos os vértices de um grafo. Se uma pessoa fosse incumbida dessa tarefa, é provável que ela adotasse um método de teste de todas as combinações possíveis para garantir a identificação dos caminhos mais curtos. O método empregado pelo algoritmo não se distancia muito dessa abordagem.

??? Atividade

Ok , mas como que o algoritimo testa todos os vértices para ter garantia que encontrou o caminho mais curto entre eles?
::: Gabarito

Para fazer isso o algoritmo testa todos os vértices para garantir que encontrou o caminho mais curto entre eles, isso é realizado por meio de loops. Esses loops são essenciais para iterar sobre todos os pares de vértices e calcular os caminhos mais curtos entre eles. É importante comentar que o loops iniciam em 0 e vai até n, sendo n a quantidade de vértices. 

:::
O código começa a ter  uma cara assim :
Floyd-Washall:
    i= primeiro vértice a ser analisado
    l=primeiro vértice a ser analisado 
    c=primeiro vértice a ser analisado
    enquanto i não for o ultimo vértice:
        enquanto l não for o ultimo vértice:
            enquanto c não for o ultimo vértice:
        


Voltando à abordagem de uma pessoa para resolver esse problema, após selecionar um vértice, ela começaria a verificar se há um caminho mais curto utilizando esse vértice como ponto de partida.
???

??? Atividade

Como você faria essa verificação?
::: Gabarito

Se sua resposta envolve checar os custos das arestas, está correta, pois, afinal, esse é o único parâmetro que determina se um caminho é realmente o mais curto.
:::

???

Agora precisamos entender como o código realiza essa tarefa, ou seja, como ele pode garantir qual caminho é realmente o mais curto.



??? Atividade

Como o codigo pode ter esta certeza de qual caminho ter o menor custo 
::: Gabarito


O algoritmo realiza essa análise por meio de uma condição que verifica se o caminho direto entre dois vértices é o mais curto, ou se o caminho do primeiro vértice ao vértice auxiliar em uso, e deste último ao vértice de destino, é mais curto.

:::

???
Adicionando essa verificação no código:
Floyd-Washall:
    i= primeiro vértice a ser analisado
    l=primeiro vértice a ser analisado 
    c=primeiro vértice a ser analisado
    enquanto i não for o ultimo vértice:
        enquanto l não for o ultimo vértice:
            enquanto c não for o ultimo vértice:
             se o caminho do vértice l ->c > o caminho do vértice l->i->c:

Se o uso deste vértice resultar em um caminho com um custo menor, o algoritmo atualiza o valor na matriz correspondente.
No final o código deverá ficar com essa cara:
Floyd-Washall:
    i= primeiro vértice a ser analisado
    l=primeiro vértice a ser analisado 
    c=primeiro vértice a ser analisado
    enquanto i não for o ultimo vértice:
        enquanto l não for o ultimo vértice:
            enquanto c não for o ultimo vértice:
             se o caminho do vértice l ->c > o caminho do vértice l->i->c:
                o custo de l->c é igual ao custo de l->i->c

Acompanhe pela animação, o que acontece com a matriz depois de cada interação do algoritimo

:Simulacao


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
