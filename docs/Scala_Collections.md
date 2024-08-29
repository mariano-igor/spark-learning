# Coleções em Scala

Scala é uma linguagem poderosa que oferece uma ampla gama de coleções para manipular dados de forma eficiente e expressiva. Esta documentação fornece uma visão geral das coleções em Scala, juntamente com exemplos de código, comparação entre diferentes coleções e suas aplicabilidades.

## Índice

1. [Introdução às Coleções](#introducao)
2. [Listas (`List`)](#listas)
3. [Arrays (`Array`)](#arrays)
4. [Sequências (`Seq`)](#sequencias)
5. [Vetores (`Vector`)](#vetores)
6. [Conjuntos (`Set`)](#conjuntos)
7. [Mapas (`Map`)](#mapas)
8. [Filas (`Queue`)](#filas)
9. [Pilhas (`Stack`)](#pilhas)
10. [Comparação entre Coleções](#comparacao)
11. [Aplicabilidade das Coleções](#aplicabilidade)
12. [Referências](#referencias)

---

## 1. Introdução às Coleções <a name="introducao"></a>

As coleções em Scala são estruturas de dados que permitem armazenar, manipular e operar sobre conjuntos de elementos. Scala oferece coleções mutáveis e imutáveis, proporcionando flexibilidade e segurança no desenvolvimento de aplicações.

### Tipos de Coleções:

- **Mutáveis**: Permitem a modificação de seus elementos após a criação.
- **Imutáveis**: Não permitem modificações após a criação. Alterações resultam na criação de uma nova coleção.

A maioria das coleções está disponível nas versões mutável (`scala.collection.mutable`) e imutável (`scala.collection.immutable`).

---

## 2. Listas (`List`) <a name="listas"></a>

### Descrição

- **Imutável**: Uma vez criada, a lista não pode ser modificada.
- **Estrutura**: Lista encadeada, onde cada elemento aponta para o próximo.

### Exemplo de Código

```scala
val nums = List(1, 2, 3, 4, 5)
val sum = nums.sum  // Soma todos os elementos
val newList = 0 :: nums  // Adiciona 0 no início da lista

println(nums)      // Saída: List(1, 2, 3, 4, 5)
println(newList)   // Saída: List(0, 1, 2, 3, 4, 5)
```

### Características

- **Tempo constante** para adicionar ou acessar o primeiro elemento.
- **Tempo linear** para acessar elementos em posições mais distantes (devido à estrutura encadeada).

### Aplicabilidade

- **Padrão de Imutabilidade**: Usada quando se deseja manter a imutabilidade.
- **Operações em Cabeçalho**: Ideal quando as operações são frequentemente realizadas no início da lista.

---

## 3. Arrays (`Array`) <a name="arrays"></a>

### Descrição

- **Mutável**: Permite modificar elementos após a criação.
- **Estrutura**: Estrutura de dados indexada, similar a arrays em outras linguagens como Java.

### Exemplo de Código

```scala
val arr = Array(1, 2, 3, 4, 5)
arr(0) = 0  // Modifica o primeiro elemento

println(arr.mkString(", "))  // Saída: 0, 2, 3, 4, 5
```

### Características

- **Acesso rápido** a qualquer elemento via índice.
- **Mutabilidade**: Elementos podem ser alterados sem criar uma nova estrutura.

### Aplicabilidade

- **Performance**: Ideal para situações que exigem acesso rápido e modificação frequente dos elementos.
- **Interoperabilidade com Java**: Facilita a integração com bibliotecas Java que requerem arrays.

---

## 4. Sequências (`Seq`) <a name="sequencias"></a>

### Descrição

- **Imutável**: Interface geral para sequências que preservam a ordem dos elementos.
- **Estrutura**: Base para outras coleções como `List` e `Vector`.

### Exemplo de Código

```scala
val seq = Seq(1, 2, 3, 4, 5)
val seqWithAddedElement = seq :+ 6  // Adiciona um elemento ao final

println(seq)  // Saída: Seq(1, 2, 3, 4, 5)
```

### Características

- **Ordem preservada**: Os elementos mantêm a ordem de inserção.
- **Interface genérica**: Oferece métodos comuns para todas as sequências.

### Aplicabilidade

- **Interface Genérica**: Usada como supertipo quando se deseja tratar diferentes sequências de maneira uniforme.
- **Preservação de Ordem**: Ideal para cenários onde a ordem dos elementos é importante.

---

## 5. Vetores (`Vector`) <a name="vetores"></a>

### Descrição

- **Imutável**: Alternativa eficiente às listas para operações de leitura.
- **Estrutura**: Implementação baseada em árvore, proporcionando bom desempenho em operações de leitura e escrita.

### Exemplo de Código

```scala
val vec = Vector(1, 2, 3, 4, 5)
val updatedVec = vec.updated(0, 0)  // Atualiza o primeiro elemento

println(vec)        // Saída: Vector(1, 2, 3, 4, 5)
println(updatedVec) // Saída: Vector(0, 2, 3, 4, 5)
```

### Características

- **Acesso rápido** a qualquer elemento, com desempenho melhor que listas para leituras aleatórias.
- **Imutabilidade**: Operações resultam em novos vetores, preservando o original.

### Aplicabilidade

- **Leituras Aleatórias Rápidas**: Ideal quando são necessárias operações frequentes de leitura em posições variadas.
- **Alternativa à Lista**: Boa escolha quando se deseja imutabilidade com acesso rápido aos elementos.

---

## 6. Conjuntos (`Set`) <a name="conjuntos"></a>

### Descrição

- **Imutável e Mutável**: Coleção sem elementos duplicados.
- **Estrutura**: Implementações baseadas em árvores ou hash tables.

### Exemplo de Código

```scala
val nums = Set(1, 2, 3, 4, 5)
val numsWithDuplicate = nums + 5  // Tentativa de adicionar um valor duplicado

println(nums)            // Saída: Set(1, 2, 3, 4, 5)
println(numsWithDuplicate) // Saída: Set(1, 2, 3, 4, 5)
```

### Características

- **Sem duplicados**: Garante que não existam elementos duplicados.
- **Operações rápidas**: Adição, remoção e verificação de presença são rápidas, especialmente em `HashSet`.

### Aplicabilidade

- **Conjuntos Únicos de Dados**: Ideal quando é necessário garantir que todos os elementos sejam únicos.
- **Operações de Conjunto**: Útil para operações como união, interseção e diferença entre conjuntos.

---

## 7. Mapas (`Map`) <a name="mapas"></a>

### Descrição

- **Imutável e Mutável**: Coleção de pares chave-valor.
- **Estrutura**: Implementações baseadas em árvores ou hash tables.

### Exemplo de Código

```scala
val ages = Map("Alice" -> 25, "Bob" -> 30)
val updatedAges = ages + ("Charlie" -> 35)  // Adiciona um novo par chave-valor

println(ages)          // Saída: Map(Alice -> 25, Bob -> 30)
println(updatedAges)   // Saída: Map(Alice -> 25, Bob -> 30, Charlie -> 35)
```

### Características

- **Chave única**: Cada chave é única, associada a exatamente um valor.
- **Busca eficiente**: Rápida recuperação de valores baseados em chaves.

### Aplicabilidade

- **Busca e Mapeamento**: Ideal para situações onde dados precisam ser acessados rapidamente por uma chave única.
- **Armazenamento de Configurações**: Útil para armazenar pares chave-valor, como configurações.

---

## 8. Filas (`Queue`) <a name="filas"></a>

### Descrição

- **Mutável e Imutável**: Coleção que segue a ordem de entrada (FIFO - First In, First Out).
- **Estrutura**: Implementações com base em listas encadeadas ou arrays circulares.

### Exemplo de Código

```scala
import scala.collection.immutable.Queue

val q = Queue(1, 2, 3)
val dequeuedQ = q.dequeue._2  // Remove o primeiro elemento da fila

println(q)          // Saída: Queue(1, 2, 3)
println(dequeuedQ)  // Saída: Queue(2, 3)
```

### Características

- **FIFO**: Acessa e remove elementos na ordem de inserção.
- **Operações constantes**: Adição

 ao final e remoção do início são operações rápidas.

### Aplicabilidade

- **Fila de Processos**: Ideal para estruturas de fila em sistemas que processam tarefas na ordem em que chegam.
- **Fluxos de Trabalho**: Útil em sistemas de processamento de dados onde a ordem de execução é crucial.

---

## 9. Pilhas (`Stack`) <a name="pilhas"></a>

### Descrição

- **Mutável e Imutável**: Coleção que segue a ordem inversa de entrada (LIFO - Last In, First Out).
- **Estrutura**: Implementações com base em listas encadeadas ou arrays.

### Exemplo de Código

```scala
import scala.collection.mutable.Stack

val stack = Stack(1, 2, 3)
stack.push(4)  // Adiciona 4 ao topo da pilha

println(stack)  // Saída: Stack(4, 1, 2, 3)
stack.pop()     // Remove o elemento do topo da pilha
println(stack)  // Saída: Stack(1, 2, 3)
```

### Características

- **LIFO**: Acessa e remove elementos na ordem inversa de inserção.
- **Operações rápidas**: Adição e remoção de elementos no topo da pilha são operações rápidas.

### Aplicabilidade

- **Desfazer/Refazer**: Ideal para implementar funcionalidades de desfazer/refazer em editores.
- **Análise de Expressões**: Útil em algoritmos de parsing que requerem análise de expressões aninhadas.

---

## 10. Comparação entre Coleções <a name="comparacao"></a>

### Tabela de Comparação

| Coleção  | Imutável/Mutável | Estrutura           | Complexidade de Acesso | Complexidade de Inserção/Remoção | Uso Comum                                     |
|----------|------------------|---------------------|------------------------|----------------------------------|------------------------------------------------|
| `List`   | Imutável          | Lista encadeada     | O(n)                    | O(1) na cabeça                   | Padrão de imutabilidade, manipulação na cabeça |
| `Array`  | Mutável           | Array indexado      | O(1)                    | O(1)                             | Processamento de dados indexados               |
| `Vector` | Imutável          | Árvore balanceada   | O(log n)                | O(log n)                         | Acesso aleatório rápido                        |
| `Set`    | Ambos             | Árvore/Hash table   | O(1) em `HashSet`       | O(1) em `HashSet`                | Conjuntos únicos de dados                      |
| `Map`    | Ambos             | Árvore/Hash table   | O(1) em `HashMap`       | O(1) em `HashMap`                | Mapeamento chave-valor                         |
| `Queue`  | Ambos             | Lista/Array         | O(n)                    | O(1) na cabeça/cauda             | Fila de processos                              |
| `Stack`  | Ambos             | Lista/Array         | O(1) no topo            | O(1) no topo                     | Algoritmos de pilha, desfazer/refazer          |

### Análise:

- **Listas** são ótimas para estruturas imutáveis com operações na cabeça.
- **Arrays** oferecem acesso rápido e são ideais para dados mutáveis.
- **Vetores** equilibram bem entre acesso rápido e imutabilidade.
- **Conjuntos** e **Mapas** são fundamentais para operações baseadas em unicidade e mapeamento.
- **Filas** e **Pilhas** são essenciais para cenários específicos de processamento de dados.

---

## 11. Aplicabilidade das Coleções <a name="aplicabilidade"></a>

### Quando usar cada coleção?

1. **List (`List`)**:
   - Use quando precisar de uma estrutura imutável e onde as operações na cabeça da lista são comuns, como em listas encadeadas ou processamento recursivo de dados.

2. **Array (`Array`)**:
   - Ideal para dados que precisam ser acessados rapidamente e modificados frequentemente, como em cálculos científicos ou manipulação de grandes datasets.

3. **Vector (`Vector`)**:
   - Utilize `Vector` quando precisar de uma coleção imutável, mas com acesso aleatório rápido. É uma boa alternativa para listas em operações de leitura.

4. **Set (`Set`)**:
   - Use `Set` quando precisar garantir a unicidade dos elementos e realizar operações de conjunto, como união e interseção.

5. **Map (`Map`)**:
   - Ideal para situações em que é necessário acessar rapidamente valores baseados em uma chave única, como em cache, armazenamento de configurações, ou mapeamento de dados.

6. **Queue (`Queue`)**:
   - Utilize `Queue` para implementar filas de processamento, onde a ordem de execução segue a ordem de chegada.

7. **Stack (`Stack`)**:
   - Use `Stack` em algoritmos onde a ordem inversa de entrada é importante, como em parsing de expressões ou implementações de desfazer/refazer.

---

## 12. Referências <a name="referencias"></a>

- [Scala Collections Documentation](https://docs.scala-lang.org/overviews/collections-2.13/introduction.html)
- [Effective Scala - Collections](https://twitter.github.io/effectivescala/#Collections)
- [Scala School - Collections](https://twitter.github.io/scala_school/collections.html)

---
