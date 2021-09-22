```python
import random
import requests
import re


# 아래처럼 출력하세요
#  01234
# 0*   *
# 1 * *
# 2  *
# 3 * *
# 4*   *
def draw_star():
    for i in range(5):
        for j in range(5):
            if i == j or i + j == 4:
                print('*', end='')
            else:
                print(' ', end='')
        print()


# 1. 10보다 작은 난수 20개를 만들고, (리스트)
# 2. 중복되지 않는 숫자만 뽑아서 새로운 리스트를 만드세요
#    [1, 3, 4, 1, 3] => [1, 3, 4]
def make_unique_1():
    ran_li, unique = [], []
    for _ in range(20):
        ran_li.append(random.randrange(1, 10))

    for i in ran_li:
        exist = False
        for j in unique:
            if i == j:
                exist = True
                break
        if not exist:
            unique.append(i)

    print(ran_li)
    print(unique)


def make_unique_2():
    ran_li, unique = [], []
    for i in range(20):
        ran_li.append(random.randrange(1, 10))
        for j in ran_li:
            if j not in unique:
                unique.append(j)

    print(ran_li)
    print(unique)


def re_weather():
    # 아래 주소로부터 데이터를 가져오세요
    # 기상청에서 제공하는 province를 찾아보세요
    url = 'http://www.kma.go.kr/weather/forecast/mid-term-rss3.jsp?stnId=108'
    received = requests.get(url)
    # print(received.text)
    province = re.findall(r'<province>(.+?)</province>', received.text)

    # location을 찾아보세요
    location = re.findall(r'<location wl_ver="3">(.+?)</location>', received.text, re.DOTALL)
    # print(province)
    # data를 찾아보세요
    for n, i in enumerate(location):
        data = re.findall(r'<data>(.+?)</data>', i, re.DOTALL)
        # mode, tmEf, wf, tmn, tmx, rnSt를 찾아보세요
        for j in data:
            mode = re.findall(r'<mode>(.+?)</mode>', j)
            tmEf = re.findall(r'<tmEf>(.+?)</tmEf>', j)
            wf = re.findall(r'<wf>(.+?)</wf>', j)
            tmn = re.findall(r'<tmn>(.+?)</tmn>', j)
            tmx = re.findall(r'<tmx>(.+?)</tmx>', j)
            rnSt = re.findall(r'<rnSt>(.+?)</rnSt>', j)
            print(f'{province[n]}:{mode[0]}:{tmEf[0]}:{wf[0]}:{tmn[0]}:{tmx[0]}:{rnSt[0]}')


# items 함수를 사용해서 key와 value를 모두 출력하세요
def basic_dict():
    d = {'name': 'kim', 'age': 25}
    for k, v in d.items():
        print(k, v)


def basic_slicing():
    a = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    # 앞쪽 절반을 출력하세요
    print(a[:len(a)//2])
    # 뒤쪽 절반을 출력하세요
    print(a[len(a)//2:])
    # 짝수 번째만 출력하세요
    print(a[::2])
    # 홀수 번째만 출력하세요
    print(a[1::2])
    # 거꾸로 출력하세요
    print(a[::-1])
    # 거꾸로 짝수 번째만 출력하세요
    print(a[-2::-2])
    # 거꾸로 홀수 번째만 출력하세요
    print(a[::-2])


def arg_max(a):
    # 리스트에서 가장 큰 숫자의 위치를 찾는 함수를 만드세요
    b = 0
    for i in range(len(a)):
        if a[i] >= a[b]:
            b = i
    return b


# arg_max 함수를 사용해서 리스트를 정렬하세요
def set_list(a):
    print(sorted(a))
    print(a)
    for i in reversed(range(len(a))):
        b = arg_max(a[:i+1])
        a[i], a[b] = a[b], a[i]
    print(a)
    # 내림차순으로 정렬하세요 (sort 함수 사용)
    a.sort(reverse=True)
    print(a)


# 문자열 리스트를 사전순으로 정렬하세요
def set_str():
    colors = ['Red', 'green', 'BLUE', 'Yellow']
    print(sorted(colors, key=lambda n: str(n).lower()))


# 기상청 파싱한 결과를 weather.txt 파일에 저장하세요
# 각각의 컬럼을 쉼표(,)로 구분해서 저장합니다
# province와 city를 findall 한번으로 찾아보세요
# mode, tmEf, wf, tmn, tmx, rnSt를 findall 한번으로 찾아보세요
def re_weather_2():
    url = 'http://www.kma.go.kr/weather/forecast/mid-term-rss3.jsp?stnId=108'
    received = requests.get(url)
    f = open('data/weather.txt', 'w', encoding='utf-8')
    # print(received.text)
    location = re.findall(r'<location.+?>(.+?)</location>', received.text, re.DOTALL)
    for i in location:
        prov_city = re.findall('<province>(.+?)</province>.+?<city>(.+?)</city>', i, re.DOTALL)
        data = re.findall(r'<data>(.+?)</data>', i, re.DOTALL)
        # print(prov_city)
        for j in data:
            etc = re.findall(r'<.+?>(.+?)</.+?>', j)
            print(f'{prov_city[0][0]},{prov_city[0][1]},{etc[0]},{etc[1]},{etc[2]},'
                  f'{etc[3]},{etc[4]},{etc[5]}', file=f)

    f.close()


# draw_star()
# make_unique_1()
# make_unique_2()
# re_weather()
# basic_dict()
# basic_slicing()
a = [21, 90, 34, 82, 76]
# arg_max(a)
# set_list(a)
# set_str()
# re_weather_2()
```

