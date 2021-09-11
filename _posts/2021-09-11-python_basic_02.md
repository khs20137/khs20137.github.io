```python
# 어떤 양수가 홀수인지 짝수인지 알려주는 함수를 만드세요
def odd_even(n):
    a = '짝수'
    if n % 2:
        a = '홀수'
    return a


# 2자리 정수를 거꾸로 뒤집어서 출력하는 함수를 만드세요
def rev(n):
    return (n // 10) + (n % 10 * 10)


# 3자리 양수를 거꾸로 뒤집는 함수를 만드세요
def rev_3(n):
    return (n // 100) + (n % 100 // 10 * 10) + (n % 10 * 100)


# 3자리 양수에 포함된 홀수 갯수를 구하세요
# 136 => 2
def cnt_odd(n):
    return n // 100 % 2 + n // 10 % 10 % 2 + n % 10 % 2


# 6자리 양수에 포함된 홀수 갯수를 구하세요
def cnt_odd_6(n):
    return cnt_odd(n // 1000) + cnt_odd(n % 1000)


# 2개의 정수 중에서 큰 숫자를 찾는 함수를 만드세요.
def find_max(a, b):
    if a > b:
        b = a
    return b


# 4개의 정수 중에서 큰 숫자를 찾는 함수를 만드세요
def find_max_4(a, b, c, d):
    # return find_max(find_max(a, b), find_max(c, d))
    return find_max(d, find_max(c, find_max(a, b)))


# 정수를 입력 받아서 양수인지 음수인지 0인지 알려주세요
def define_num(n):
    define = '제로'
    if n > 0:
        define = '양수'
    elif n < 0:
        define = '음수'

    return define


# 4개의 정수 중에서 가장 큰 숫자를 찾는 함수를 만드세요 (다른 함수 사용 금지)
def find_max_4(a, b, c, d):
    if a > b:
        b = a
    if c > b:
        b = c
    if d > b:
        b = d

    return b


# 학점을 계산하는 함수를 만드세요
# A : 90점 이상
# B : 80점 이상
# C : 70점 이상
# D : 60점 이상
# F : 60점 미만
def score(n):
    if n < 0 or n > 100:
        return 'X'
    grade = 'F'
    if n >= 60:
        grade = 'D'
    if n >= 70:
        grade = 'C'
    if n >= 80:
        grade = 'B'
    if n >= 90:
        grade = 'A'

    return grade


# 아래 코드를 확장해서 3번 반복하도록 만드세요
i = 0
if i < 3:
    print(i, 'lunch')
    i += 1
    if i < 3:
        print(i, 'lunch')
        i += 1
        if i < 3:
            print(i, 'lunch')
            i += 1
            if i < 3:
                print(i, 'lunch')
                i += 1


def repeat(n):
    while n < 3:
        print(n, 'lunch')
        n += 1


# 100보다 작은 양수 중에서 홀수만 출력하세요
def out_odd():
    for i in range(1, 100, 2):
        print(i)


# 0부터 24까지 출력하세요 (한 줄에 5개씩)
def out_5():
    for i in range(0, 25):
        print(i, end=' ')
        if i % 5 == 4:
            print()

    for i in range(0, 25, 5):
        print(i, i + 1, i + 2, i + 3, i + 4)


# 양수의 약수를 출력하는 함수를 만드세요
def out_divisor(n):
    # for i in range(1, n + 1):
    #     if n % i == 0:
    #         print(i, n // i)

    i = 1
    while i ** 2 <= n:
        if n % i == 0:
            print(i, n // i)
        i += 1


print(odd_even(5))
print(odd_even(8))
print(rev(56))
print(rev_3(874))
print()
print(cnt_odd(572))
print(cnt_odd_6(752831))
print()
print(find_max(5, 9))
print(find_max(9, 5))
print(find_max_4(5, 8, 2, 5))
print(find_max_4(8, 2, 5, 5))
print(find_max_4(2, 5, 5, 8))
print(find_max_4(5, 5, 8, 2))


print(define_num(5))
print(define_num(-5))
print(define_num(0))
print(find_max_4(5, 3, 9, 1))
print(find_max_4(1, 5, 3, 9))
print(find_max_4(9, 1, 5, 3))
print(find_max_4(3, 9, 1, 5))

scores = [110, -13, 0, 65, 78, 88, 95]
for i in scores:
    print(score(i))

repeat(n=0)

out_odd()
out_5()
out_divisor(24)


```

