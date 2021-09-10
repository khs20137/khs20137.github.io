```python
---
layout: post
title:  "python basic1"
---


# "hello, python!" 을 3번 출력하는 코드를 만드세요(3 가지)
print('"hello, pytho!"' * 3)
print('"hello, pytho!"' '"hello, pytho!"' '"hello, pytho!"')
print('"hello, pytho!"', '"hello, pytho!"', '"hello, pytho!"')

# 퀴즈
# 'hello' 와 "hello"를 출력하세요(따옴표 포함)
print("'hello'", '"hello"', '\'hello\'', '\"hello\"')

# 퀴즈
# a와 b의 값을 교환 하세요 (2가지)
# 두개의 컵에 든 내용물을 섞지 않고 옮기는 법.
a = 3
b = 5
c = a
a = b
b = c
a, b = b, a

# 퀴즈
# 산술 연산자 7개를 적용하세요
print(a + b)
print(a - b)
print(a / b)
print(a * b)
print(a // b)
print(a % b)
print(a ** b)

# 퀴즈
# +와 - 연산자를 사용해서 추가 변수 없이 교환하세요.
a = a + b
b = a - b
a = a - b

# 퀴즈
# a를 b로 나눈 나머지를 구하세요(% 연산자 사용금지)
a - (a // b * b)

# 퀴즈
# 아래 코드가 에러나지 않도록 수정하세요
# print(s + 2)
s = 'dinner'
print(s + '2')
print(s + str(2))

# 퀴즈
# 관계 연산 6가지를 a와 b에 대해 적용하세요.
a > b
a < b
a >= b
a <= b
a == b
a != b

# 퀴즈
# age 변수가 10대인지 아닌지 알려주세요.
age = 17
9 < age < 20
a = age > 9
b = age < 20

a + b > 1
a == b
a * b


```