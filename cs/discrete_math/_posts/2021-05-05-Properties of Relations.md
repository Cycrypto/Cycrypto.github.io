---
layout: post
title: Discrete_math
slug: discrete_math
description: >
  관계의 속성에 대해 학습한다.
sitemap: false
hide_last_modified: true
---

## Properties of Relations



### OverView

* [Relations on Sets (집합의 관계)](#Relations on Sets)
* [Reflexivity(반사 관계), Symmetry(대칭 관계) and Transitivity (이행 관계)](#Reflexivity, Symmetry, and Transitivity)
* [Equivalence Relations (동치 관계)](#Equivalence Relation)

  



### Relations on Sets

#### Definition

> $$A, B$$가 집합이라고 하자.<br>
> **A Binary Relation R from A to B** is a subset of $$A \times B$$<br>
>
> $${}_x\mathrm{R}_{y} \Leftrightarrow (x, y) \in R \cdots$$  x, y가 집합 R과 관계가 있다<br>
> $$_x\mathrm{\not{R}}_{y} \Leftrightarrow (x, y) \notin R \cdots$$  x, y가 집합 R과 관계가 없다





#### Example

> `2로 나눈 나머지가 같은 관계 (The Congruence Modulo 2 Relation)` <br>
>
> For all$$ (m, n) \in Z \times Z, \, _mE_n \Leftrightarrow m - n $$ is even



> `원 에서의 관계 (Example the Circle Relation)`<br>
>
> $$C$$ from $$R \times R$$ as follows:<br>
>
> For any $$(x,y) \in R \times R, (x,y) \in C \Leftrightarrow x^2 + y^2 = 1$$





### Relations and Functions

#### Definition

> 함수 $$F$$는 집합 $$A$$에서 집합 $$B$$로 가는 관계이며, 아래의 두 성질을 만족한다.<br>
>
> 1. For every element $$x$$ in $$A$$, there is an element $$y$$ in B such that $$(x,y)\in F$$<br>
> 2. For all element $$x$$ in $$A$$ and $$y$$ and $$z$$ in B<br>
>    if $$(x, y) \in F$$ and $$(x, z) \in F$$, then $$y = z$$,<br>
>    If is a function from $$A$$ to $$B$$<br>
>    $$Y = F(x) \Leftrightarrow (x,y) \in F$$





#### Example

> `유한 집합에서의 함수의 관계`
>
> $$A = \{2,4,6\}, B = \{1,3,5\}$$<br>
>
> 1. $$R = \{(2, 5), (4, 1), (4, 3), (6, 5)\}$$<br>
>
>    `한 element가 가르키는 요소가 2개가 되면 안되므로, 함수가 아니다.`<br>
>
> 2. For all $$(x,y) \in A \times B, (x,y) \in S \Leftrightarrow y = x+1$$<br>
>    `Domain에서 내보내는 요소가 없는 경우가 있으므로 함수가 아니다`<br>



### The Inverse of a Relation

#### Definition

> $$R$$ be a relation from $$A$$ to $$B$$ <br>
>
> Define $$R^{-1}$$ from $$B$$ to $$A$$ 는 아래 조건을 따른다.<br>
>
>  $$R^{-1} = \{(y,x) \in B \times A | (x, y) \in R\}$$



### Representation of Binary Relation

#### Definition

> * Arrow Diagram
> * Relation Matrix
> * Directed graph





### N-ary Relation and Relational Databases

####  Definition

> 집합 $$A_1, A_2\cdots,A_n$$이 n-ary relation $$R$$ on $$A_1 \times A_2 \times \cdots \times A_n$$이 각자의 부분집합일때 binary, ternary quaternary relations...  라고 부름.



### Reflexivity, Symmetry, and Transitivity

> `Reflexivity` : 모든 관계가 자기 자신과 관련이 있음<br>
> $$R$$ is *reflexive* if, and only if, for all $$x \in A,\, _xR_x$$<br>



> `Symmetry` : 한 원소가 다른 원소와 관계가 있으면, 두번째 원소는 첫번째 원소와 관계가 있다.<br>$$R$$ is *symmetric* if, and only if, for all $$x, y \in A$$, if $$_xR_y $$then $$_yR_x$$<br>



> `Transitivity` : 첫번쨰 원소가 두번째와 관련이 있고, 두번쨰 원소가 세번째와 관련이 있다면 첫번째 원소는 세번째와 관련되어있다.<br>
>
> $$R$$ is *transitive* if, and only if, for all $$x, y \in A, $$ if  $$_xR_y $$ and $$ _yR_z  $$ then $$  _xR_z$$<br>





### Property of Relations on Infinite Sets



#### To prove the relations ins Reflexive, Symmetric, or Transitive ...

> 이항관계(Binary Relation) $$R$$이 무한 집합 $$A$$에 있다고 가정하자.
>
> 예를 들어, `symmetric`에 대하여
>
> $$\forall x, y \in, if _xR_y $$ then $$_yR_X$$
>
> 특정한 경우로 명제를 다시 써보면,
>
> 실수 집합의 동치 관계에서 다시쓴 명제는 $$\forall x, y \in R,$$ if $$x=y$$ then $$y=x$$



### The Transitive Closure of a Relation

#### Definition

> $$A$$를 집합이라 하고 $$R$$을 $$A$$의 이항 관계라고 하자.
>
> *The Transitive closure of *$$R$$ 은 이항 관계 $$A$$ 의 $$R^t$$ 이고 아래 조건을 만족한다,
>
> 1. $$R^t$$ is transitive.
> 2. $$R \subseteq R^t$$.
> 3. if $$S$$ is any other transitive relation that contains $$R$$, then $$R^t \subseteq S$$ 



### Equivalence Relation

#### Definition

> 집합 $$A$$의 partition 이 주어졌다면,  binary relation은 $$A$$로 정의된 partition $$R$$을 포함한다
>
> for all $$x, y \in A$$
>
> $$_xR_y \Leftrightarrow $$ There is a subset $$A$$ of the partition such that both $$x$$ and $$y$$ are in $$A$$.



#### Definition2

> Let $$A$$ be a set with a partition and let $$R$$ be the relation induced by partition.
>
> Then, $$R$$ is reflexive, symmetric, and transitive.
>
> * A를 집합이라 하고, R을 A의 Relation이라고 하자.
>
>    R이 **equivalence relation**이라고 할때, R은 reflexive, symmetric, transtive 하다.





#### Notation of an Equivalence Relation

> Let $$m$$ and $$n$$ be integers and let $$d$$ be a positive integer.
>
> The notation $$m \equiv n (mod\, d)$$ is read m is congruent to n modulo d
>
> $$d | (m-n)$$
>
> Symbolically,
>
> $$m \equiv n (mod\, d) \Leftrightarrow d | (m - n)$$



### Equivalence Classes of an Equivalence Relation

#### Definition

> $$A$$를 $$R$$의 집합이라고 가정하고, $$R$$을 $$A$$의 동치관계라고 할때,
>
> A에 있는 각각의 원소들은 *The Equivalence Class of a*라고 하고,
>
> denoted $$[a]$$ , called *the class of a for short, is the set of all elements x in A such that x is related to a by R*

**Symbolically**

$$[a] = \{x \in A \| _xR_a\}$$라고 표기한다.









