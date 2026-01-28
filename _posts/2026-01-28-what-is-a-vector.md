---
title: "Reconstructing Linear Algebra (2): What Is a Vector?"
date: 2026-01-27
categories: [linear-algebra]
tags: [linear-algebra, vector, abstraction, thinking]
layout: single
author_profile: true
read_time: true
comments: false
share: true
---

Calculus나 Physics에서는  
vector를 *magnitude와 direction을 동시에 갖는 quantity*라고 배운다.

그런데 Computer Science에서는  
왜 array나 tuple을 vector와 거의 동일하게 다룰까?

---

Linear Algebra의 절반은 vector라고 해도 과언이 아니다.  
하지만 이공계 과목들을 두루 경험한 사람이라면  
한 번쯤 이런 의문을 가져봤을 것이다.

*왜 과목마다 vector의 정의가 다를까?*  
심지어 Linear Algebra 교재 안에서도  
진도에 따라 vector를 다르게 설명하지 않는가?

나 역시 같은 혼란을 겪었고,  
‘진짜 vector의 정의’를 찾으려 노력했다.

이 글에서는  
- vector의 **수학적 정의가 무엇인지**,  
- 그리고 **왜 각 학문에서 vector를 다르게 정의하는지**를  
이야기해보려 한다.

조금 수학적이고,  
특히 집합론적인 이야기가 포함되어 있다.

---

Vector를 정의하려면  
먼저 vector space를 알아야 하고,  
vector space를 정의하려면 field가 필요하다.

개념 하나를 정의하기 위해  
여러 개의 개념이 연쇄적으로 등장하는 구조는  
처음에는 꽤 부담스럽게 느껴질 수 있다.

하지만 수학은 본질적으로 bottom-up 학문이다.  
기초 위에만  
일관된 논의를 쌓아 올릴 수 있다.

그래서 잠시,  
교과서처럼 정의부터 적어보자.

---

## Definition: Field

A **field** \( \mathbb{F} \) is a set equipped with two operations,  
called addition \( + \) and multiplication \( \cdot \), such that:

### (1) Addition
- \( a + b = b + a \)
- \( (a + b) + c = a + (b + c) \)
- There exists \( 0 \in \mathbb{F} \) such that \( a + 0 = a \)
- For each \( a \in \mathbb{F} \), there exists \( -a \in \mathbb{F} \)

### (2) Multiplication
- \( ab = ba \)
- \( (ab)c = a(bc) \)
- There exists \( 1 \in \mathbb{F}, 1 \neq 0 \), such that \( a1 = a \)
- For each \( a \neq 0 \), there exists \( a^{-1} \in \mathbb{F} \)

### (3) Distributivity
- \( a(b + c) = ab + ac \)

---

## Definition: Vector Space

Let \( \mathbb{F} \) be a field.  
A **vector space** \( V \) over \( \mathbb{F} \) is a set equipped with:

- vector addition \( + : V \times V \to V \)
- scalar multiplication \( \cdot : \mathbb{F} \times V \to V \)

such that for all \( \boldsymbol{u}, \boldsymbol{v}, \boldsymbol{w} \in V \)  
and all \( a, b \in \mathbb{F} \):

### (1) Vector addition
- \( \boldsymbol{u} + \boldsymbol{v} = \boldsymbol{v} + \boldsymbol{u} \)
- \( (\boldsymbol{u} + \boldsymbol{v}) + \boldsymbol{w} = \boldsymbol{u} + (\boldsymbol{v} + \boldsymbol{w}) \)
- There exists \( \boldsymbol{0} \in V \) such that \( \boldsymbol{v} + \boldsymbol{0} = \boldsymbol{v} \)
- For each \( \boldsymbol{v} \in V \), there exists \( -\boldsymbol{v} \in V \)

### (2) Scalar multiplication
- \( a(b\boldsymbol{v}) = (ab)\boldsymbol{v} \)
- \( 1\boldsymbol{v} = \boldsymbol{v} \)

### (3) Distributive properties
- \( a(\boldsymbol{u} + \boldsymbol{v}) = a\boldsymbol{u} + a\boldsymbol{v} \)
- \( (a + b)\boldsymbol{v} = a\boldsymbol{v} + b\boldsymbol{v} \)

---

## Definition: Vector

An element of a vector space is called a **vector**.

---

처음 이 정의들을 접했을 때,  
나는 솔직히 거의 아무것도 와닿지 않았다.

무슨 말인지도 잘 모르겠고,  
왜 이렇게까지 복잡해야 하는지도 이해되지 않았다.

하지만 여러 번 읽고,  
이후에 전개되는 내용들을 따라가다 보니  
조금씩 이 정의들이 왜 필요한지 이해하게 되었다.

---

이제, 조금 더 편하게 말해보자.

**Linear Algebra에서 vector란,  
addition과 scalar multiplication이 정의된 수학적 object이다.**

Physics에서 말하는  
*magnitude와 direction을 가진 vector* 역시,  
이 두 연산을 자연스럽게 만족한다.

그렇다면 Computer Science에서 다루는  
array나 tuple은 어떨까?

element-wise하게 addition과 scalar multiplication을 정의하면  
이들 역시 vector space의 공리를 만족한다.

즉, 이들 모두  
Linear Algebra에서 말하는 **vector**다.

더 나아가면  
function, sequence, matrix, 심지어 tensor까지도  
vector로 취급할 수 있다.

---

그래서 나는  
Linear Algebra에서의 vector를 이렇게 이해하게 되었다.

> **Vector란,  
> Physics와 Computer Science를 포함한  
> 다양한 분야에서 활용될 수 있도록  
> 일반화된 개념이다.**

---

그렇다면 이런 질문이 자연스럽게 따라온다.

*처음부터 모든 학문에서  
이렇게 일반적인 정의를 쓰면 되지 않았을까?*

나 역시 그렇게 생각했다.  
개념을 깊이 이해하면,  
분명 더 넓은 문제를 바라볼 수 있을 것이라 믿는다.

하지만 앞에서 보았듯이,  
vector 하나를 정의하기 위해  
field, scalar, vector space 같은 개념들이 필요하다.

이는 학습의 진입 장벽을 크게 높인다.

그래서 나는 이것을  
**일종의 encapsulation**이라고 생각하게 되었다.

각 학문은  
자신의 목적에 맞게  
vector의 본질을 감추고,  
활용하기 쉬운 형태로 정의한 것이다.

---

Vector의 여러 정의와,  
그것들을 하나로 묶는 일반적인 정의를 공부하며  
나는 한 가지 생각에 도달했다.

세상을 이해하고 바꾸는 engineer는  
지식을 그 자체로 소비하지 않는다.

Physics, Calculus, Computer Science에서  
vector의 형태와 목적이 서로 다르듯,  
우리는 개념을  
목적에 맞게 해석하고 변형할 수 있어야 한다.

학문은  
그 자체로 존재할 때보다,  
문제 해결을 위해 활용될 때  
비로소 빛난다고 나는 믿는다.
