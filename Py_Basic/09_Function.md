# Function
- **한 가지 기능**을 하는 코드 묶음
    - `function definition` : 함수의 `Prototype`을 정하는 것 
        - `parameterization` : parameter와 return값을 정하는 것
    - `function call` : 함수 사용하는 것
- 구조화 $\Rightarrow$ 가독성 $\Rightarrow$ 유지/보수 수월
-  기존 코드 설계시부터 함수로 작성 / 코드 작성 후 재구조화 $\Rightarrow$ `Refactoring`
```py
# function definition syntax example
def function1(a, b): 
    something = ...
    <statement>
    <statement>
    ...
    ...
    return something

# function call
result = function(3, 5)
```

## 내장함수
- `len()`
    - length 출력 함수
    ```py
    s = "I need Python."
    L = [1, 2, 3, 4, 5]

    len(s), len(L) # 출력 : 14 5 
    ```
- `type`
    - 특정 변수의 데이터 타입을 알고 싶은 경우 사용하는 함수
    ```py
    # 데이터를 ','를 붙여 나열하면 기본적으로 튜플로 인식
    t = 1, 2
    s = '\n'
    x = 0xCOFFEE

    type(t), type(s), type(x) # 출력 : tuple, str, int
    ```
- `print()`
    - 옵션
        - default : new 라인
        - end : 출력 후 해야 할 사항 지정
            - print(i, end=" ") : 결과값을 옆으로 나열
        ```py
        s = "Hello World"
        for c in s:
            print(c, end=" ")
            # print(c, end="")
        ```
    - file 형태로 출력
        ```py
        # 파일 생성
        with open("sample_file.txt", 'w') as f:
            # 모니터가 아닌 파일에 출력
            print("Hello World", file=f)
        ```
- `input()`
    - 특정 입력을 사용자로부터 받음
    - 입력을 받으면 무조건 문자로 받음
    ```py
    data = input("여러 개의 숫자를 입력하시오: ").split(',') # 입력 : 1,2,3,4,5
    data # 출력 : ['1', '2', '3', '4', '5']
    ```
- `sorted()`
    - 다양한 시퀀스를 정렬
    - 알파벳 > 숫자 순서
    - 집합의 경우, 정렬하여 list로 반환
    ```py
    L = [1, 3, 6, 1, -55, 145]
    s = 'hello'
    t = ('a', '123', 'he')
    ss = {1, 2, 10, -1, 4}

    sorted(L) # 출력 : [-55, 1, 1, 3, 6, 145]
    sorted(s) # 출력 : ['e', 'h', 'l', 'l', 'o']
    sorted(t) # 출력 : [-1, 1, 4, 10]
    # 본래 집합에는 순서 개념이 없지만 sorted 가능
    sorted(ss) # 출력 : [-1, 1, 2, 4, 10]

    ```

## Parameterization
1. parameter와 return이 모두 존재하는 경우
    - 가장 흔하게 사용되는 경우
    ```py
    def add(a, b):
        return a + b

    add(3, 5)              # 출력 : 8
    add('a', 'b')          # 출력 : 'ab'
    add([1, 2], [3, 4, 5]) # 출력 : [1, 2, 3, 4, 5]
    ```
1. parameter의 개수를 모르는 경우
    - parameter definition 단계에서 *args를 사용 $\Rightarrow$ args 이름으로 input 파라미터가 전부 튜플로 들어옴
    ```py
    def add_many(*args):
        total = 0
        for arg in args:
            total += arg
        return total
        
        # 위의 코드와 동일
        # return sum(args)
    
    add_many(1, 2, 3, 5)
    add_many(2, 4)
    add_many(432, 466, 263, 232, 654, 223)
    ```
1. parameter의 유입 여부를 모르는 경우
    - `formatted string` 사용
    - parameter definition 단계에서 default 값 지정
    ```py
    def get_str(name, grade='C', year=2022):
        s = f"The student named {name} received an {grade} grade in {year}"
        return s

    get_str("Ellie")
    ```    

## function call 주의 사항
```py
L1 = [1, 2, 3] # mutable data type
t = (1, 2, 3) # immutable data type

def change_things(data):
    data[0] = 'update'
    
    return data

L2 = change_things(L1)
# 원본까지 바뀌어 버림
print(L1) # 출력 : ['update', 2, 3]
print(L2) # 출력 : ['update', 2, 3]
t = change_things(t) # Type Error: 'tuple' object does not support item assignment
print(t)
```
1. mutable data type을 Parameter로 넘겨주는 경우, 내부 데이터가 바뀔 수 있음을 인지해야 함
    - mutable type의 파라미터로 들어오면 원본도 번형
    - 원본의 변경을 원하지 않을 경우
        - [방법1] 내부적으로 변환해서 사용하는 코드 작성 후 input을 튜플로 넘겨줌
            ```py

            ```
        - [방법2] 명시적으로 L의 복사본을 넘김(`copy()` 이용)
            ```py
            L1 = [1, 2, 3]

            def change_things(data):
                data[0] = 'update'
                
                return data

            L2 = L1.copy()
            change_things(L2)
            print(L1) # 출력 : [1, 2, 3]
            print(L2) # 출력 : ['update', 2, 3]
            ``` 
1. immutable data type은 내부 데이터가 바뀌지 않음
    ```py
    t = (1, 2, 3)

    # 위 코드에서 immutable에 대한 typeError 수정
    def change_things(data):
        data = list(data)
        data[0] = 'update

        return data

    t = change_things(t)
    print(t)
    ```

