```python
import random
import re


# 정수의 자릿수를 구하는 함수를 만드세요 (0 <= N < 10000)
# 1. return은 1회 사용
# 2. elif 사용시 반드시 확인
# 범위를 벗어난 값이 들어오면 -1 반환
def num_digit(n):
    digit = 1
    # if n >= 10:
    #     digit = 2
    # if n >= 100:
    #     digit = 3
    # if n >= 1000:
    #     digit = 4
    # if n >= 10000:
    #     digit = 'inf'

    while n > 0:
        n //= 10
        if n == 0:
            break
        digit += 1

    return digit


# 0이상이고 100보다 작은 난수를 지정한 횟수만큼 만들어서 홀수만 출력하는 함수를 만드세요
def odd_out(n):
    for i in range(n):
        m = random.randrange(0, 100)
        if m % 2:
            print(m)


# 지정한 횟수만큼의 난수를 발생시켜서 홀수 합계와 짝수 합계를 각각 구하는 함수를 만드세요
# 3 9 4 6 7
# 홀수 19
# 짝수 10
def sum_num(n):
    odd, even = 0, 0
    for i in range(n):
        m = random.randrange(0, 100)
        if m % 2:
            odd += m
            print('홀수 :', m)
        else:
            even += m
            print('짝수 :', m)

    print(odd, even)


# 100보다 작은 난수 10개짜리 리스트를 반환하는 함수를 만드세요 (2가지)
def get_random_list():
    random_list = []
    for i in range(10):
        random_list.append(random.randrange(100))

    ran_list = []
    for i in range(10):
        ran_list += [random.randrange(100)]

    return random_list
    # return ran_list
    # return [random.randrange(100) for _ in range(10)]


# 리스트를 거꾸로 출력하는 함수를 만드세요
def rev_list(li):
    li_rev_1 = []
    for i in range(len(li)-1, -1, -1):
        li_rev_1.append(li[i])

    li_rev_2 = []
    for i in reversed(range(len(li))):
        li_rev_2.append(li[i])

    print(li_rev_1)
    print(li_rev_2)
    print(li[::-1])


# 리스트를 거꾸로 뒤집는 함수를 만드세요
def rev_list_out(li):
    # for i in range(len(li)-1, len(li)//2-1, -1):
    #     li[len(li)-1 - i], li[i] = li[i], li[len(li)-1 - i]

    for i in range(len(li)//2):
        li[len(li)-1-i], li[i] = li[i], li[len(li)-1-i]

    return li


# poem.txt 파일에 대해 읽고 쓰는 연습을 합니다
def read_write():
    f = open('D:\python\\tensorflow2.5\ME\data\poem.txt', 'r', encoding='utf-8')
    w = open('D:\python\\tensorflow2.5\ME\data\sample.txt', 'w', encoding='utf-8')

    # readlines 함수로 읽은 내용을 줄 단위로 깨끗하게 출력하세요
    # for row in f.readlines():
    #     print(row.strip())

    # readline 함수로 읽어서 출력합니다
    while True:
        line = f.readline()
        print(line.strip())
        if not line:
            break

    f.close()
    w.close()


# 파일을 읽어서 반환하는 함수를 만드세요
# (파일 전체를 하나의 문자열로 반환합니다)
def ret_text():
    f = open('D:\python\\tensorflow2.5\\ME\data\poem.txt', 'r', encoding='utf-8')
    text = ''
    for row in f.readlines():
        text += row

    f.close()

    # return f.read()
    return text


# poem.txt 파일을 거꾸로 출력하세요
def rev_text():
    f = open('D:\python\\tensorflow2.5\ME\data\poem.txt', 'r', encoding='utf-8')

    # for i in reversed(f.read()):
    #     print(i, end='')

    row = ''
    for i in f.readlines():
        row += i

    f.close()

    for i in range(len(row)):
        print(row[len(row)-i-1], end='')


# poem.txt 파일을 sample.txt 파일에 복사하는 함수를 만드세요
def copy_text():
    f = open('D:\python\\tensorflow2.5\ME\data\poem.txt', 'r', encoding='utf-8')
    w = open('D:\python\\tensorflow2.5\ME\data\sample.txt', 'w', encoding='utf-8')

    for line in f:
        w.write(line)

    f.close()
    w.close()


# 아래와 같이 출력하세요
# 0
# 0 1
# 0 1 2
# 0 1 2 3
# 0 1 2 3 4
num = ''
for i in range(5):
    num += str(i) + ' '
    print(num)

# 아래와 같은 모양으로 출력하세요
# *****
# *****
# *****
# *****

# print('*****')를 반복문으로 바꾸세요
for _ in range(4):
    for _ in range(5):
        print('*', end='')
    print()

# 아래처럼 출력하세요
# 0 1 2 3 4
# 1 2 3 4 5
# 2 3 4 5 6
# 3 4 5 6 7
# 4 5 6 7 8
for i in range(5):
    for j in range(5):
        print(j + i, end=' ')
    print()

# 아래처럼 출력하세요
#  0123
# 0*
# 1**
# 2***
# 3****

# ****
# ***
# **
# *

#    *
#   **
#  ***
# ****

# ****
#  ***
#   **
#    *
for i in range(4):
    for j in range(4):
        if j <= i:
            print('*', end='')
        else:
            print(' ', end='')
    print()

# for i in range(4, -1, -1):
for i in reversed(range(4)):
    for j in range(4):
        if j < i:
            print('*', end='')
        else:
            print(' ', end='')
    print()

for i in range(4):
    # for j in range(4, -1, -1):
    for j in reversed(range(4)):
        if j < i:
            print('*', end='')
        else:
            print(' ', end='')
    print()

# for i in range(4, -1, -1):
for i in reversed(range(4)):
    # for j in range(4, -1, -1):
    for j in reversed(range(4)):
        if j < i:
            print('*', end='')
        else:
            print(' ', end='')
    print()


db = '''3412    [Bob] 123
3834  Jonny 333
1248   Kate 634
1423   Tony 567
2567  Peter 435
3567  Alice 535
1548  Kerry 534'''

# 숫자 1개를 찾아보세요
num = re.findall(r'[0-9]', db)
print(num)

# 전화번호와 회사 아이디를 찾아보세요
phone_id = re.findall(r'[0-9]+', db)
print(phone_id)

# 이름만 찾아보세요
name = re.findall(r'[A-Z][a-z]+', db)
# name = re.findall(r'[A-Za-z]+', db)
print(name)

# T로 시작하는 이름을 찾아보세요
the_name = re.findall(r'T[a-z]+', db)
print(the_name)

# T로 시작하지 않는 이름을 찾아보세요
except_name = re.findall(r'[A-SU-Z][a-z]+', db)
print(except_name)


print(num_digit(0))
print(num_digit(7565))
print(num_digit(10000))
print(num_digit(1029834745000))
print()
odd_out(4)
print()
sum_num(7)

random.seed(6)
ran_list = get_random_list()
print(ran_list)
rev_list(ran_list)
print(rev_list_out(ran_list))

# read_write()
# text = ret_text()
# rev_text()
copy_text()

```