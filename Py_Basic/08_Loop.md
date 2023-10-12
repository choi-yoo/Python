# Loop

## while statement
- 조건에 의한 반복 수행시 사용
```py
number = 1
while 1 <= number <= 9:
    print(f"2 x {number} = {2*number}")
    number = number + 1 
```

## for statement
- 반복 횟수 지정하는 방법
    1. `range()` 사용해 직접 설정
        - 횟수를 자동으로 만들어주는 기능
        ```py
        # 1부터 5전까지 출력
        for i in range(1, 5):
            print(i, end=' ') # 출력 : 1 2 3 4

        # for i in range(0, 4)와 동일 
        for i in range(4):
            print(i, end=' ') # 출력 : 0 1 2 3
        ```
    1. `iteratable object`(ex. 리스트) 사용해 연속형 데이터 타입 변수 설정
        ```py
        L = [1, 2, 3]

        # L이라는 리스트를 i가 순서대로 반복하라는 명령어
        for i in L:
            print(L[i], end=' ') # 출력 : 1 2 3
        ```
- `List comprehension`
    - 특정 리스트 생성 방법
    ```py
    L = ['1234', '111', '07001']
    for i in range(len(L)):
        L[i] = int(L[i]) + 3
    print(L)

    # list comprehension
    L2 = ['1234', '111', '07001']
    L2 = [int(i) + 3  for i in L2]
    print(L2)
    ```