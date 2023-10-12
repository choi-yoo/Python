# Dict
```py
codebook = {'John' : '0011', 'Maria' : '1234'}
codebook['John'] # 출력 : '0011'
```
- `key-value pair`
    - 특정 key 값으로 특정 value 값을 대응해서 나타내는 구조
- dict는 {} 안에 `:`과 `,`을 사용함

## key 값 사용시 주요 포인트
1. key는 정수뿐만 아니라 다른 것도 사용 가능
1. key는 절대 중복이 있으면 안됨
    - 문법적 오류는 아니나, 중복된 것에 대한 다른 처리가 있음을 알아야 함
1. 수정 불가
    - immutable(tuple, int, float, str)로만 key값으로 사용 가능

```py
# 빈 사전
D = {}

# key-value pair add
D['a'] = 3
D # 출력 : {'a' : 3}

# key-value pair update
D['a'] = 5
D # 출력 : {'a' : 5}

# key가 겹칠 경우, 뒤에 만들어진 것만 살아남음
D2 = {'a' : 1, 'a' : 2, 'b' : 3} 
D2 # 출력 : {'a' : 2, 'b' : 3} 
```

## `in` operator
- sequence에 해당 데이터가 존재하는지 확인
- 사전의 경우 key값을 대상으로 확인
- 리스트, 튜플, 집합, 문자열에 대해서는 해당 원소가 존재하는지 확인
```py
D = {'a' : 5, 'b' : 7}

"phone" in D # 출력 : False
'a' in D     # 출력 : True
7 in D       # 출력 : False, key값만 가능
```
```py
# 리스트, 튜플, 집합에서도 테스트
L = [1, 2, 3]
t = [4, 5, 6]
s = {7, 8, 9}
st = "Hello World"

1 in L    # 출력 : True
4 in t    # 출력 : True
4 in s    # 출력 : False
# substring match
'He' in st # 출력 : True
```