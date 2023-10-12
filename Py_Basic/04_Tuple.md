# 2. Tuple
```py
t = (1, 3.14, 'a')
t[0] # 출력 : 1

# 원소 변경 불가
t[1] = 5 # 출력 : TypeError: 'tuple' object does not support item assignment
```
- 특징
    - list와 유사
        - indexing, slicing 모두 사용 가능
        - 원소 자유롭게 사용 가능
            - concatenation 가능
        - 연산 가능(`+`, `*`)
    - list와 차이
        1. 튜플은 `()` 사용
            - vs. list는 [] 사용
            - 메모리에 있어 효율적(리스트는 생성시 넉넉하게 메모리를 잡기 때문)
        1. `immutable` : 생성 후 변경 불가
            - update 불가
            - vs. list는 `mutable` : 생성 후 변경 가능
