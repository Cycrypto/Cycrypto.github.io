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
* Partial Order Relations (전 후 관계가 있는 관계)



### Modular Arithmetic with Applications to Cryptography

#### Cryptography

> `Plaintext` $$\rightarrow$$ `Ciphertext`$$\rightarrow$$`Plaintext`



#### Example

* 시저 암호 : 알파벳을 지정된 만큼 이동하여 encryption 함.

  * 각 글자의 빈도수를 알면 쉽게 해독 가능.
  
* RSA 암호 : 최초의 공개 키 암호 시스템.

  * Congruence modulo n 이라는 특징을 알 필요가 있음.

    > *Modular Equivalence*
    >
    > Let a, b and n be any integers and suppose n > 1
    >
    > The following statements are all equivalent:
    >
    > 1. $$n\|(a-b)$$.
    > 2. $$a \equiv b(mod n)$$.
    > 3. $$a = b _ kn$$ for some integer $$k$$
    > 4. $$a$$ and $$b$$ have the same (nonnegative) remainder when divided by $$n$$
    > 5. $$a\, mod\, n = b\, mod\, n$$ .

  