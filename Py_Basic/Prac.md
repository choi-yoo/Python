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

# 뉴스 기사로 워드클라우드 그려보기
- `WordCloud` : 단어의 빈도를 체크해 시각적으로 표현하는 방식
    - 빈도 분석을 위해 데이터를 전부 **단어 단위**로 나눠야 함
```py
# news.txt파일 불러오기
from wordcloud import WordCloud
from collections import Counter

with open("../input/programming/news.txt", 'r') as f:
    news = f.read()

news = news.split()

# Counter() : 단어 단위로 쪼개는 함수
counts = Counter(news)

# most_common() : 카운트에서 가장 많이 등장한 것을 튜플 형태로 제시
# most_common의 인수 값은 많이 나온 값들을 몇 개까지 끊을 것인지
# words = counts.most_common(50)

# 워드 클라우드 빈도수 지정
wc = WordCloud(width = 800,
               height = 600,
               background_color = 'white',
               ).generate_from_frequencies(counts)


# words에 대한 워드 클라우드 생성 방법
wc1 = WordCloud(width = 800,
                height = 600,
                background_color = 'white',
                ).generate_from_frequencies(dict(words))
```
```py
# 만든 워드 클라우드 출력
# matplot 라이브러리
import matplotlib.pyplot as plt

plt.figure(figsize(10, 6))
plt.axis(False) # 테투리가 없어짐
plit.imshow(wc1)

# 워드 클라우드 저장
plit.savefig('wordcloud.png')
```