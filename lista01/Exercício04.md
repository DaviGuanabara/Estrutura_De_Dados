## Estrutura de Dados - Lista 01 - Exercício 04.

### 1. Equipamento e linguagem utilizada.

Foi utilizado o google colab, assim os algoritmos foram escritos em python.

### 2. Descrição do algoritmo.

Nesse exercício, foi utilizado dois métodos, iterativo e recursivo, para os dois problemas citados: os números de fibonacci e de josefo.

Os números de fibonacci são uma sequencia de números no qual a o seu valor é resultado da soma dois dois números anteriores. A sequência inicia-se com 0 e 1, assim, os primeiros números de fibonacci são: 
0, 1, 1, 2, 3, 5, 8, 13, 21...

Já os números de josefo estão relacionados com o a solução para o problema de Flávio Josefo, o qual consiste em saber em qual posição de um circulo deve-se posicionar para sobrevier a uma sequencia alternada de execução. Como os seus números, tem-se:
Para 00 integrante(s): 0
Para 01 integrante(s): 1
Para 02 integrante(s): 1
Para 03 integrante(s): 3
Para 04 integrante(s): 1
Para 05 integrante(s): 3
Para 06 integrante(s): 5
Para 07 integrante(s): 7
Para 08 integrante(s): 1
Para 09 integrante(s): 3
Para 10 integrante(s): 5

A implementação desses algoritmos está escrita abaixo:

Fibonacci Recursivo
```python
def fiboRec(n):
    if n==1:
        return 0
    elif n==2:
        return 1
    else:
        return fiboRec(n-1) + fiboRec(n-2)
```

Fibonacci Iterativo
```python
def fiboRec(n):
    if n==1:
        return 0
    elif n==2:
        return 1
    else:
        return fiboRec(n-1) + fiboRec(n-2)
```

Josefos Recursivo
```python
def fiboRec(n):
    if n==1:
        return 0
    elif n==2:
        return 1
    else:
        return fiboRec(n-1) + fiboRec(n-2)
```

Josefos Iterativo
```python
def fiboRec(n):
    if n==1:
        return 0
    elif n==2:
        return 1
    else:
        return fiboRec(n-1) + fiboRec(n-2)
```

### 3. Dizer como procedeu a contagem do tempo.


Foi criado uma função de teste, no qual a mesma recebe um objeto com os dois métodos do algoritmo a ser avaliado e a ordem do último número. Marca o tempo antes e depois da execução, calcula a diferença do tempo e mostra, ao final. o tempo utilizado. Para evitar que o tempo demandado para execução dos testes de números de ordem acima de 30 invialibilassem os testes, foi escolhido que a variação da ordem seria de 4 em 4, e não sequencial.
A implementação do algoritmo pode ser vista a seguir.

```python

import time


def timeSpent(func, iteractions):
    
    print("Function: " + func.name)
    print("i    Iterative    Recursive")

    times = [];

    for i in range(2, iteractions, 4):
        times = []
        for attr in ('iterative', 'recursive'):
   
            start_time = time.time()
            getattr(f1, attr)(i)
            end_time=time.time()

            times.append("{:.6f}".format(end_time - start_time))
        
        print("%d   %s    %s  " % (i, times[0], times[1]))


class Func:
  def __init__(self, funcName, funcIterative, funcRecursive):
    self.iterative = funcIterative
    self.recursive = funcRecursive
    self.name = funcName
```

### Tabela com duas colunas, na primeira o valor de n e na segunda o tempo medido para determinar o valor de Fn.
### Compare os tempos dos algoritmos que ir a implementar, usando o mesmo equipamento e linguagem.

Para facilitar a comparação entre o tempo gasto dos dois métodos de um algoritmo, fora feita uma pequena modificação na tabela proposta. De tal forma que resultou em uma tabela com 3 colunas: a primeira contendo a ordem; a segunda com o tempo necessário para executar com o método iterativo; e a terceira com o tempo de execução do método recursivo.

#### Tabela Fibonacci
Ordem | Iterative (seg) | Recursive (seg)
------|-----------------|-----------------
02    |    0.000007     | 0.000005    
06    |    0.000006     | 0.000009  
10    |    0.000005     | 0.000044  
14    |    0.000005     | 0.000168  
18    |    0.000006     | 0.004966  
22    |    0.000005     | 0.005693  
26    |    0.000004     | 0.038947  
30    |    0.000008     | 0.283306  
34    |    0.000016     | 1.896107  
38    |    0.000009     | 12.798490  
42    |    0.000020     | 87.920402 


#### Tabela Josephus Problem
Ordem | Iterative (seg) | Recursive (seg)
------|-----------------|-----------------
02    |     0.000006    | 0.000002  
06    |     0.000004    | 0.000006  
10    |     0.000003    | 0.000033  
14    |     0.000003    | 0.000149  
18    |     0.000008    | 0.000862  
22    |     0.000008    | 0.006602  
26    |     0.000008    | 0.042871  
30    |     0.000016    | 0.280490  
34    |     0.000015    | 1.898122  
38    |     0.000017    | 12.889854
42    |     0.000018    | 87.955633  


### Estabeleça conclusões sobre os tempos que obteve, note que o importante  e ter a rela c~ao entre os tempos.

Conforme a ordem do número buscado aumenta, cresce também o tempo demandado para que o algoritmo seja executado. Porém, os algoritmos iterativos ampliam o tempo demandado de forma linear, diferente dos recursivos, no qual o tempo demandado elevam-se exponencialmente. O que nos mostra o alto grau de eficiência que os algoritmos iterativos têm em prol dos recursivos.
