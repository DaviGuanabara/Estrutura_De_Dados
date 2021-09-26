## Estrutura de Dados - Lista 01 - Exercício 04.

### 1. Equipamento e linguagem utilizada.

Foi utilizado o google colab, assim os algoritmos foram escritos em python.

### 2. Descrição do algoritmo.

Nesse exercício, foi utilizado dois métodos, iterativo e recursivo, para os dois problemas citados: os números de fibonacci e os de josefo.

Os números de fibonacci são uma sequencia de números no qual o seu valor é resultado da soma dos dois números anteriores. A sequência inicia-se com 0 e 1, e assim, os primeiros números de fibonacci são: 
0, 1, 1, 2, 3, 5, 8, 13, 21...

Abaixo está a implementação desse algoritmo em python.

[Fibonacci Recursivo](https://www.pythonprogressivo.net/2018/10/Como-Gerar-Sequencia-Fibonacci-Recursao.html#:~:text=Gerando%20a%20Sequ%C3%AAncia%20de%20Fibonacci,obtido%20somando%20os%20dois%20anteriores.&text=Ent%C3%A3o%20uma%20fun%C3%A7%C3%A3o%20exibe%20todos,at%C3%A9%20o%20n%2D%C3%A9simo%20termo.)
```python
def fiboRec(n):
    if n==1:
        return 0
    elif n==2:
        return 1
    else:
        return fiboRec(n-1) + fiboRec(n-2)
```

[Fibonacci Iterativo](https://stackoverflow.com/questions/15047116/an-iterative-algorithm-for-fibonacci-numbers)
```python
def fiboIt(n):
    a, b = 0, 1

    for i in range(1, n):
        a, b = b, a + b
    return a
```

Já os números de josefo estão relacionados com o a solução para o problema de Flávio Josefo, o qual consiste em saber em qual posição de um circulo deve-se posicionar para sobrevier a uma sequencia alternada de execução. Com os seus números, tem-se:
Para 00 integrante(s), posição do sobrevivente: 0
Para 01 integrante(s), posição do sobrevivente: 1
Para 02 integrante(s), posição do sobrevivente: 1
Para 03 integrante(s), posição do sobrevivente: 3
Para 04 integrante(s), posição do sobrevivente: 1
Para 05 integrante(s), posição do sobrevivente: 3
Para 06 integrante(s), posição do sobrevivente: 5
Para 07 integrante(s), posição do sobrevivente: 7
Para 08 integrante(s), posição do sobrevivente: 1
Para 09 integrante(s), posição do sobrevivente: 3
Para 10 integrante(s), posição do sobrevivente: 5

O algoritmo para solucionar o problema de josefo consiste em remover da sequencia os números restantes de forma alternada. Assim, para uma sequência de 5 números [1, 2, 3, 4, 5], a remoção se dará da seguinte forma:

####Tabela 01 - Ordem de remoção.
Número | Lista           
-------|-----------------
2      |  [1, , 3, 4, 5]  
4      |  [1, , 3,  , 5]
1      |  [ , , 3,  , 5]
5      |  [ , , 3,  ,  ]

Assim, como mostrado na Tabela 01, o número de josefo para uma sequência de 5 números é o 3.
Abaixo está a implementação desse algoritmo em python.

[Josefo Recursivo](https://www.geeksforgeeks.org/josephus-problem-set-1-a-on-solution/#:~:text=The%20problem%20has%20following%20recursive%20structure.&text=After%20the%20first%20person%20(kth,from%20k%25n%20%2B%201.)

```python
def fiboRec(n):
    if n==1:
        return 0
    elif n==2:
        return 1
    else:
        return fiboRec(n-1) + fiboRec(n-2)
```

[Josefo Iterativo](https://www.geeksforgeeks.org/josephus-problem-iterative-solution/)
```python
def josephusIterative(n, k = 2):
      sum = 0;

      for val in range(2,n+1):
          sum = (sum + k) % val;

      return sum+1;
```

### 3. Dizer como procedeu a contagem do tempo.


Foi criado uma função de teste, no qual a mesma recebe um objeto com os dois métodos do algoritmo a ser avaliado e a ordem do último número. Marca o tempo antes e depois da execução, calcula a diferença do tempo e mostra, ao final, uma tablea com o tempo utilizado. Para evitar que o tempo demandado com a execução dos testes de números de ordem acima de 30 inviabilisassem os testes, fora determinado que a variação da ordem seria de 4 em 4, e não sequencial.
A implementação do teste pode ser vista a seguir.

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


f1 = Func("Fibonacci", fiboIt, fiboRec)
f2 = Func("Josephus Problem", josephusIterative, josephusRecursive)

iteractions = 44
timeSpent(f1, iteractions)
timeSpent(f2, iteractions)
```

### Tabela com duas colunas, na primeira o valor de n e na segunda o tempo medido para determinar o valor de Fn.



#### Tabela 02 - Tempos Fibonacci Iterativo
Ordem | Iterative (seg) 
------|-----------------
02    |    0.000007      
06    |    0.000006       
10    |    0.000005    
14    |    0.000005      
18    |    0.000006      
22    |    0.000005    
26    |    0.000004     
30    |    0.000008     
34    |    0.000016     
38    |    0.000009    
42    |    0.000020


#### Tabela 03 - Tempos Fibonacci Recursivo
Ordem | Recursive (seg)
------|-----------------
02    | 0.000005    
06    | 0.000009  
10    | 0.000044  
14    | 0.000168  
18    | 0.004966  
22    | 0.005693  
26    | 0.038947  
30    | 0.283306  
34    | 1.896107  
38    | 12.798490  
42    | 87.920402 


#### Tabela 04 - Tempos Problema de Josefo Iterativo
Ordem | Iterative (seg) 
------|-----------------
02    |     0.000006    
06    |     0.000004    
10    |     0.000003    
14    |     0.000003     
18    |     0.000008    
22    |     0.000008    
26    |     0.000008      
30    |     0.000016  
34    |     0.000015 
38    |     0.000017 
42    |     0.000018 

#### Tabela 05 - Tempos Problema de Josefo Recursivo
Ordem | Recursive (seg)
------|-----------------
02    | 0.000002  
06    | 0.000006  
10    | 0.000033  
14    | 0.000149  
18    | 0.000862  
22    | 0.006602  
26    | 0.042871  
30    | 0.280490  
34    | 1.898122  
38    | 12.889854
42    | 87.955633 


### Compare os tempos dos algoritmos que ir a implementar, usando o mesmo equipamento e linguagem.

Para facilitar a comparação entre o tempo gasto dos dois métodos de um algoritmo, fora feita uma pequena melhoria na tabela proposta. De tal forma que resultou em uma tabela com 3 colunas: a primeira contendo a ordem; a segunda com o tempo necessário para executar com o método iterativo; e a terceira com o tempo de execução do método recursivo.

#### Tabela 06 - Comparação de métodos com Fibonacci
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


#### Tabela 07 - Comparação de métodos com o Problema de Josefo
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
