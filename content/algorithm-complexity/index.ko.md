+++
title = "알고리즘 복잡도"
date = 2025-11-01
updated = 2025-11-01
description = "알고리즘의 시간 및 공간 복잡도를 수학적 표기법으로 이해하기."
tags = ["algorithms", "complexity", "computer-science", "math"]
+++

알고리즘 복잡도를 이해하는 것은 효율적인 코드를 작성하는 데 중요합니다. 우리는 알고리즘이 어떻게 확장되는지를 표현하기 위해 수학적 표기법을 사용합니다.

## 빅 오 표기법

빅 오 표기법은 알고리즘의 성장률의 상한을 설명합니다. 여기 일반적인 복잡도 클래스들이 있습니다:

### 상수 시간 - O(1)

{% math() %}
f(n) = O(1)
{% end %}

입력 크기에 관계없이 동일한 시간을 취하는 연산.

### 로그 시간 - O(log n)

{% math() %}
f(n) = O(\log n)
{% end %}

각 반복마다 문제가 반으로 나누어지는 이진 검색 알고리즘에서 일반적입니다.

### 선형 시간 - O(n)

{% math() %}
f(n) = O(n)
{% end %}

배열을 반복하는 것처럼 입력 크기에 선형으로 확장되는 알고리즘.

### 선형 로그 시간 - O(n log n)

{% math() %}
f(n) = O(n \log n)
{% end %}

병합 정렬과 퀵 정렬과 같은 효율적인 정렬 알고리즘이 이 복잡도를 가집니다.

### 2차 시간 - O(n²)

{% math() %}
f(n) = O(n^2)
{% end %}

중첩 루프는 종종 2차 복잡도를 초래합니다.

## 수학적 공식

### 첫 n개의 자연수의 합

{% math() %}
\sum_{i=1}^{n} i = \frac{n(n+1)}{2}
{% end %}

### 기하급수

{% math() %}
\sum_{i=0}^{n} r^i = \frac{r^{n+1} - 1}{r - 1} \quad \text{for } r \neq 1
{% end %}

### 마스터 정리

형식 T(n) = aT(n/b) + f(n)의 재귀 관계에 대해:

{% math() %}
T(n) = \begin{cases}
\Theta(n^{\log_b a}) & \text{if } f(n) = O(n^{\log_b a - \epsilon}) \\
\Theta(n^{\log_b a} \log n) & \text{if } f(n) = \Theta(n^{\log_b a}) \\
\Theta(f(n)) & \text{if } f(n) = \Omega(n^{\log_b a + \epsilon})
\end{cases}
{% end %}

## 공간 복잡도

공간 복잡도는 메모리 사용을 측정합니다. 예를 들어, 재귀 알고리즘은 스택 공간을 사용합니다:

{% math() %}
S(n) = O(h)
{% end %}

여기서 $h$는 재귀 트리의 높이입니다.

## 분할 상환 분석

연산 시퀀스에 대한 연산당 평균 시간:

{% math() %}
\text{분할 상환 비용} = \frac{\text{총 비용}}{n}
{% end %}

이러한 수학적 기초를 이해하면 알고리즘을 효과적으로 분석하고 최적화할 수 있습니다.