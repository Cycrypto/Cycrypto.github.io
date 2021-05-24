---
layout: post
title: Discrete_math
slug: discrete_math
description: >
  관계의 속성에 대해 학습한다.
sitemap: false
hide_last_modified: true
---

## Properties of Relations 2

### OverView

* [Modular Arithmetic with Applications to Cryptography(나머지 연산이 암호학에 적용이 되는가)](#Modular Arithmetic with Applications to Cryptography)
* [partial Order Relations (전 후 관계가 있는 관계)](#Partial Order Relations)



### Modular Arithmetic with Applications to Cryptography

#### Cryptography

> `Plaintext` $$\rightarrow$$ `Ciphertext`$$\rightarrow$$`Plaintext`



#### Example

* 시저 암호 : 알파벳을 지정된 만큼 이동하여 encryption 함.

  * 각 글자의 빈도수를 알면 쉽게 해독 가능.
  
* <mark>RSA 암호 </mark>: 최초의 공개 키 암호 시스템.  

  

  * Congruence modulo n 이라는 특징을 알 필요가 있음. (모듈러 합동)
  
    > *Modular Equivalence*(모듈러 동치)
    >
    > Let $$a$$, $$b$$ and $$n$$ be any integers and suppose $$n > 1$$
    >
    > The following statements are all equivalent:
    >
    > 1. $$n\vert(a-b)$$.
    > 2. $$a \equiv b(mod n)$$.
    > 3. $$a = b _ kn$$ for some integer $$k$$
    > 4. $$a$$ and $$b$$ have the same (nonnegative) remainder when divided by $$n$$
    > 5. $$a\, mod\, n = b\, mod\, n$$ .
    
    
    
    > if $$n$$ is any integer with $$n > 1$$, congruence modulo n is an equivalence relation on the set of all integers.
    >
    > $$a = 0, 1, 2, \cdots, n-1$$ then,  
    > $$[a] = \{m \in Z \vert m \equiv a(mod n)\}$$
    
      
    
    
    
  * Modular Arithmetic
  
    > Let a, b, c, d and n be integer with n  > 1, and suppose
    >
    > $$a \equiv c (mod\, n) and b \equiv d(mod\, n)$$ Then,
    >
    > 1. $$(a + b) \equiv (c + d)(mod\, n)$$.
    > 2. $$(a - b) \equiv (c-d)(mod\, n)$$.
    > 3. $$ab \equiv cd (mod\, n)$$.
    > 4. $$a^m \equiv c^m (mod\, n)$$ for all positive integers m.
  
  * **Definition**
  
    > Integers $$a$$ and $$b$$ are **relatively prime**(서로소) iff, $$gcd(a,b) = 1$$
    
    
    
  * > **Encrypto**  
    > 두 개의 아주 큰 *prime numbers* p,  q 선택,  
    >
    > ex)
    >
    > ALICE 는 $$p = 5, q = 11 $$이고, $$pq = 55$$, $$(p-1)(q-1)$$과 서로소인 정수 $$e$$ 선택, 즉 40과 서로소인 3을 $$e$$로 선택하고, $$pq, e$$  는 *public key*로 배포함.
    >
    > $$C = M^e mod\, pq$$
    >
    > Bob이 Alice에게 "HI"라는 메시지를 보내길 원함. (H = 8, I = 9)
    >
    > $$C = 8^3 mod\, 55 = 512 mod 55 = 17$$ (H)
    >
    > $$C = 9^3 mod \, 55 = 729 mod 55 =  14$$(I)
    >
    > $$\therefore$$HI = 17 14
  
    
  
  * > **Decrypto**
    >
    > 메시지로 받은 
    > "17 14"를 해독하려고 함.
    >
    > $$M = C^d mod \, pq$$이고, $$d$$는 $$(p-1)(q-1)$$로 나눈 나머지가 $$e$$인 것의 `inverse` 한다.
    >
    > $$1 = 40 - 13 \times e$$ (공개키 40과 1을 나오게 만들어주는 k값 13 을 빼준 수를 d) 라고 하자.
    >
    > $$40 - 13 = 27 = d$$.
    >
    > $$M + kpq \equiv M(mod \, pq)$$ ($$M$$은 $$pq$$보단 작아야 하며, 실제론 $$p,\, q$$가 매우 크므로 상관 없음.)
    >
    >  $$\therefore 17^{27} mod \, 55 = 17^{16+8+2+1} mod \, 55$$이므로
    >
    > $$[16 \times 26 \times 14 \times 17] mod\, 55 = 8 mod \, 55$$



### Finding an Inverse Modulo n

> 정수 a와 음이아닌 정수 n이 있고, 정수 s가 존재 할 때 $$as \equiv 1 (mod\, n)$$이 성립한다면 s는 *an inverse for a modulo n*이라고 한다.

* 만약 $$a$$와 $$b$$가 서로소 관계이고, 정수 $$s$$와 $$t$$가 존재할 떄
  $$as + bt = 1$$이다.



#### Euclid' s Lemma

> For all integers $$a,\, b, \, c$$, if $$gcd(a,c) = 1$$ and $$a \vert bc, $$ then $$a \vert b$$



#### Cancellation Theorem for Modular Congruence

> For all integers $$a,\, b, \, c, \, n$$, if $$gcd(c,n) = 1$$ and $$ac \equiv bc(mod \, n)$$, then $$a \equiv b(mod\, n)$$



#### Fremat's Little Theorem

> If $$p$$ is any prime number and $$a$$ is any integer such that $$p \cancel{\vert} a$$, then $$a^{p-1} \equiv 1 (mod\, p)$$





### Partial Order Relations

#### Definition

> $$R$$이 집합 $$A$$의 관계라고 하자.
>
> $$R$$은 *antisymmetric* iff, for all $$a \text{ and } b \text{ in } A$$, if $$_aR_b \text{ and } _bR_a$$then a=b