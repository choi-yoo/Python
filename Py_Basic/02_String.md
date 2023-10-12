# String Data Types
## 문자열 규칙
- `""" """`
    ```py
    # 파이썬은 한 줄 단위로 실행하기에
    # 여러 줄어 걸쳐 문자열 입력시, 따옴표 세번 입력
    str = """To Be Great is
    To Be Misunderstood.
    - Ralph Waldo Emerson.
    """
    print(str)
    ```
- `' '`과 `" "`
    ```py
    # ''과 "" 모두 제공
    s1 = "I am a boy"
    s2 = 'I am a girl'
    ```
- 문자열 연산
    1. `+`
        ```py
        # concatenation
        s1 = "Hello,"
        s2 = "World!"
        s = s1 + ' ' + s2
        print(s)
        ```
    1. `*`
        ```py
        // 문자열이 반복되어 출력
        s1 = '-'
        s1 * 10
        ```
## 문자열 Formatting
- 문자열 출력시 특정 format 지정하고 싶은 경우 사용
- 문자열 포맷 방법 
    1. `str.format()` 
        - 변수가 들어갈 곳에 {}를 작성
        - 따옴표 끝나자마자 .format(변수, ...) 형식
        ```py
        fruit = "apples"
        count = 5

        print("There are {} {}".format(count, fruit))
        ```
    1. `f-string`
        - {} 안에 바로 변수 작성
        ```py
        fruit = "apples"
        count = 5

        print(f"There are {count} {fruit}.")
        ```

## 문자열 함수
- `upper()`, `lower()`
    - 대소문자 바꾸기
    ```py
    s = "Hello, World"
    # 모든 문자를 대문자로
    s.upper() # 출력 : "HELLO, WORLD"
    # 모든 문자를 소문자로
    s.lower() # 출력 : "hello, world"
    ```
- `strip()`
    - 문자 공백 지우기
    - 앞 뒤의 공백만 지운다
    - 문장 내의 공백은 지우지 않음
    ```py
    s = "        I go to school.        "
    s.strip() # 출력 : "I go to school"
    ```
- `join()`
    - 지정된 문자를 이용해 잘려있는 문자열 붙여 씀
    ```py
    s = ("010", "1234", "5678")
    '-'.join(s) # 출력 : "010-1234-5678"
    ```

- `split()`
    - 빈칸 기준으로 텍스트 나누기
    ```py
    s = "Life is too short"
    s.split() # 출력 : ['Life', 'is', 'too', 'short']

    # 특정 문자를 기준으로 나누고 싶다면 인수 이용
    s.split("is") # 출력 : ['Life ', ' too short']
    ```

- `replace()`
    - 특정 단어를 특정 단어로 변경
    ```py
    s = "Life is too short"
    s.replce("Life", "This pencil") # 출력 : "This pencil is too short"
    
    # 응용 : 빈칸 모두 지우기
    s.replce(" ", "") # 출력 : "Lifeistooshort"
    ```

- `format()`
    ```py
    fruit = "apples"
    count = 100

    s = "There are {} {}."
    s.format(count, fruit) # 출력 : 'There are 100 apples.'
    ```

- `isdigit()`
    - 숫자인지 확인
    ```py
    s = "01012345678"
    s.isdigit() # 출력 : True
    ```
- `isalnum`
    - 숫자인지 알파벳인지 확인
    ```py
    s = "HelloWorld"
    s.isalnum() # 출력 : True
    ```