# Exception Handling

## try except 구문
- 예상하지 못한 에러 발생 시, 프로그램이 멈추지 않도록 하는 구문
```py
# 입력 값이 숫자여야만 하는 상황에서의 예외 처리
# 그러나 이러한 방법은 다른 예외에서도 실행된다는 문제가 있음
try:
    money = int(input("Input a money: "))
# 에러가 발생할 경우 아래의 예외 처리 해줌    
except :
    print("Please enter a number.")
    # try문을 다시 실행
    continue
```

## 예외처리를 할 때, 특정 예외만 지정해서 사용 가능
1. `IndexError`
    - 인덱스의 범위를 초과할 때 발생하는 오류
    ```py
    L = [1, 2, 3, 4, 5]
    
    try:
        print(L[5])
    # IndexError인 경우에만 핸들링하도록 지시
    except IndexError:
        print("You have entered an incorrect index.")
    ```
1. `ZeroDivisionError`
    - 어떤 특정 숫자로 나눌 때, 숫자에 0이 들어간 경우에 발생하는 오류
    ```py
    def divide(dividend, divisor):
        try:
            return dividend / divisor
        except ZeroDivisionError:
            print("divisor cannot be zero.")

    divide(1, 0)
    ```

1. `TypeError`
    - 타입이 다른 두 개를 더할 때 발생하는 오류
    ```py
    def add(a, b):
        try:
            return a + b
        except TypeError:
            print("The types of 'a' and 'b' do not match. They must be of the same type for addition to be possible.")
    
    add('a' + 3)
    ```