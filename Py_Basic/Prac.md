# 주민등록번호 가리기
- [방법1] replace() 사용
    - 가려할 숫자를 미리 알아야 함
    ```py
    human_id = "200112-3111111"

    human_id.replace('111111', '******')
    # 출력 : 200112-3******
    ```

- [방법2] slicing()과 concatenation 사용
    ```py
    human_id = "200112-3111111"

    human_id[:8] + '******'
    humna_id[0:-6] + '******'
    # 출력 : 200112-3******
    ```

# 먹을 수 있는 음료
- [방법1] index 사용
    ```py
    coffees = ['Americano', 'Caffe' 'Latte', 'Caffe Mocha', 'Vanilla Latte', 'Hand Drip', 'Cold Brew']
    prices = [4100, 4600, 5100, 6000, 5000]

    for i in range(len(coffees)):
        if prices[i] <= 5000:
            print(coffees[i])
    ```
- [방법2] enumerate() 사용
    - `enumerate()` : for문에 index, element가 튜플 형태로 건너옴
    ```py
    coffees = [Americano, Caffe Latte, Caffe Mocha, Vanilla Latte, Hand Drip, Cold Brew]
    prices = [4100, 4600, 5100, 6000, 5000]

    for i, price in enumerate(prices):
        if price <= 5000:
            print(coffees[i])
    ```
- [방법3] zip() 사용
    - `zip()` : **동일한 크기**를 가지는 리스트를 묶어주는 함수
    ```py
    coffees = [Americano, Caffe Latte, Caffe Mocha, Vanilla Latte, Hand Drip, Cold Brew]
    prices = [4100, 4600, 5100, 6000, 5000]

    for price, coffee  in zip(prices, coffees):
        if price <= 5000:
            print(coffee)
    ```

# 배수 출력
> 1에서 100 사이 숫자 중 5의 배수를 찾아라!
- [방법1] range() 사용
    ```py
    for number in range(1, 101):
        if number % 5 ==0:
            print(number, end=' ')
    ```
- [방법2] range() 응용
    ```py
    for number in range(0, 101, 5):
        if number == 0:
            continue
        print(number, end=' ')
    ```

