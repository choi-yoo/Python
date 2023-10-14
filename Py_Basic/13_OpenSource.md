# Open Sources

## PyPI : Python Package Index
- 파이썬으로 만든 파이썬 패키지 저장소 $\Rightarrow$ 오픈소스 라이브러리 사용
- `!python --version`
    - 파이썬 버전 확인
- `!pip list`
    - 사용가능한 라이브러리 리스트 명령어
    - `pip list` : PyPI로 가져올 수 있는 라이브러리의 세팅
- `pip install "packagename"`
    - 패키지 설치 명령어
    ```ruby
    # tslean(time series learn)
    $ pip install tslearn
    ```
    ```py
    import tslearn
    from tslean.clustering import TimeSeriesKMeans
    ```
## 종류
- TensorFlow : 구글이 배포한 딥러닝 관련 오픈소스
- PhTorch
- Azure

## glob
- 파이썬에서 자동으로 파일 목록을 가져와 사용할 수 있도록 해주는 라이브러리
```py
# glob 함수 기본 사용법1
import glob
glob.glob("경로")

# glob 함수 기본 사용법2
## glob.glob()을 사용하기 번거로우니
form glob import glob
glob("경로")
```
- 특정 경로를 가지고 오는 패턴 사용
    - `*.jpg` : 지정된 폴더 안의 모든 jpg 형식의 파일 가져옴
    ```py

    glob("../input/pictures/*.jpg")
    ```

## os
- 특정 os가 제공하는 여러 기능 사용
- 업무 자동화 관련 라이브러리
    - 경로 찾기
    - 파일 존재 확인
    - 파일 옮기기
    - 환경설정 확인
    - 운영체제 정보 확인
- [Reference](https://docs.python.org/ko/3/library/os.html)
```py
import os

# 현재 사용하고 있는 환경의 CPU 코어 개수
os.cpu_count()

# 현재 운영체제 세팅
os.environ
os.environ['LANG']

# 해당 경로에 있는 데이터 확인을 위한 명령어
os.path.exists("../input")
```

## sys
- interpreter 세팅을 확인 가능한 라이브러리
```py
import sys

# 시스템 레벨에서 확인할 수 있는 변수 확인
sys.path
sys.path.append("../~")

# 시스템이 실행될 때 파이썬 인터프리터가 실행한 파이썬 파일들과 데이터
## argv(argument variable)
sys.argv

# 파이썬 인터프리터가 불러와서 쓰고 있는 모듈
## import한 라이브러리가 sys.modules에 없다면, 시스템이 모듈을 못 찾고 있음을 의미(에러 발생)
sys.modules
```

## Image
- `pillow` : PIL이라는 외부 라이브러리를 사용하는 라이브러리
    - pillow 라이브러리 내의 `Image 모듈`을 통해 기본적인 이미지 처리 가능
```py
from PIL import Image

image_path = "../input/clothes_images/001.jpg"

img = Image.open(image_path)

# properties
img.width
img.height
img.mode
img.filename # 데이터 실제 이름 확인

# 데이터 변환
## resample의 방법들 : NEAREST, BOX, BILINEAR, BICUBIC, HAMMING, LANCZOC 등
img.resize((220,220), Image.Resampling.BILINEAR)
```

## OpenCV
- 이미지 처리를 위한 라이브러리
- C++, Java, Python 등 지원
    - `opencv-python` : 파이썬에서 opencv를 이용할 수 있는 라이브러리
- load하면 자동으로 numpy **array**로 로드함
```ruby
# 설치
$ !pip install opencv-python
```
```py
# 불러오는 방법
import cv2
import matplotlib.pyplot as plt

# imread() : cv2에 있는 이미지를 read하는 함수
## 픽셀 값들이 불러와짐, dtype=unit8으로 데이터 표시
img = cv2.imread("../input/clothes_image/001.jpg")

# normalization :  0과 1 사이의 값으로 바뀜
## 보통 이미지는 255.0이라는 것으로 나눠서 처리
img = img / 255.0

# shape : 해상도와 사용 컬러 채널 확인 가능
img.shape # 출력 예시 : (1750, 1166, 3)

# cv2.resize() : 입력된 크기로 해당 데이터를 resize해주는 함수
cv2.resize(img, (224, 224))
img.shape # 출력 예시 : (224, 224, 3)

# figure(figsize=()) : 이미지 크기 조절 가능
plt.figure(figsize=(12, 8))
# axis를 False로 표시하면 축이 표시X
plt.axis(False)
# imshow() : cv2에서 이미지를 출력하는 함수
plt.imshow(img)
```
1. color $\rightarrow$ gray
    - OpenCV의 기본 컬러 = `BGR`(Blue, Green, Red)
    - `cvtColor` : 주어진 소스 파일을 원하는 형태의 코드를 넣어 변경
    ```py
    sample = "../input/clothes_image/001.jpg"

    img = cv2.imread(sample)
    # gray로 변환
    img2 = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
    # 변경 후 항상 cmap을 작성해야 선택한 색으로 출력됨
    plt.imshow(img2, cmap="gray")
    ```
1. brightness(밝기) 조절
    - more brighter $\rightarrow$ add value
    - more darker $\rightarrow$ subtract value
    ```py
    import numpy as np    

    brightness = 100
    # np.fill() : 특정 value를 가지는 numpy array 생성
    # 수치값을 지정하면 지정한 수치값이 들어간 full 매트릭스 생성
    # add 연산은 np.unit8에서 dtype을 똑같이 맞춰줘야 실행됨
    brightness_map = np.full(img.shape, brightness, dtype=np.unit8)

    brighter = cv2.add(img, brightness_map)
    darker = cv2.subtract(img, brightness_map)

    plt.imshow(brighter)
    plt.imshow(darker)
    ```

## re(regular expression)
- 정규 표현식 연산 관련 라이브러리
```py
import re

re.findall()

re.sub() # substitution

re.search()

# vs.str.split() 
# 패턴에 부합하는 토큰을 골라서 자를 수 있음
re.split()
```
```py
# 20 newsgroups

# sklean : 머신러닝 라이브러리 
from sklearn.datasets import fetch_20newsgroups

# .data라고 써서 데이터만 추출
news = fetch_20newsgroups().data
type(news) # 출력 : list
len(news) # 출력 : 11314

news_sample = news[0]

# alphabet 빼고 모두 제거하자!
re.sub('[^A-Za-z ]', '', news_sample)

# 이메일
## 영단어&숫자&특수문자 @ 영어 . 영어
## 구글링 : 정규표현식 이메일
email_patturn = ""

# 전화번호
phoneNumber_patturn = "/^\d{3}-\d{3, 4}-\d{4}$/"  
```


## random
- `random.seed` : 난수 생성 시, 기본적으로 필요한 기본 값
```py
import random

# randint() : 숫자 중 하나를 랜덤하게 추출, 인수 양쪽을 포함함
## for문을 이용할 때 숫자가 중복될 수도 있음
L = []
for i in range(6):
    n = random.randint(1, 46)
    L.append(n)

# 중복 허용 
random.choice()
L1 = random.choices(list(range(1, 47)), k=6) # 출력 : [27, 41, 9, 22, 27, 25]

# 중복 허용X
L2 = random.sample(list(range(1, 47)), k=6)
```

## Counter
- 주어져 있는 어떤 객체의 개수를 셀 수 있음
- Counter를 dictionary로 만들면 바로 데이터 출력 가능
```py
from collections import Counter

L = ['a', 'a', 'a', 'b', 'b', 'c', 'd']
D = Counter(L) # 출력 : Counter({'a': 3, 'b': 2, 'c': 1, 'd': 1})
D['a'] # 출력 : 3
```
```py
from sklearn.datasets import fetch_20newsgroups
import re

news_sample = fetch_20newsgroups().data[0]

# 대소문자 통일 후, 특수문자 및 숫자 제거
news_sample = news_sample.lower()
news_sample = re.sub('[^A-Za-z ]', '', news_sample)
# 단어별로
Counter(new_sample.split())
```

## defaultdict
- 존재하지 않는 키를 입력해도 설정한 디폴트 값을 기준으로 dictionary에 추가
- 어트리뷰트의 초기값 제공
```py
from coolections import defaultdict
from sklearn.datasets import fetch_20newsgroups
import re

news_sample = fetch_20newsgroups().data[0]
news_sample = news_sample.lower()
news_sample = re.sub('[^A-Za-z ]', '', news_sample)
news_sample = news_sample.split()

# word_dict = {} # key:val = word:count

# for문을 통해 단어를 가져와 key value로 추가
# for word in news_sample:
#     # 초기값
#     if word not in word_dict:
#         word_dict[word] = 1
#     else:
#         word_dict[word] += 1

# 초기값이 있도록 defaultdict 사용
word_dict = defaultdict(int) # 0
# word_dict = defaultdict(str) # ''
# word_dict = defaultdict(list) # []
# word_dict = defaultdict(set) # set()
# word_dict = defaultdict(dict) # {}

for word in news_sample:
    word_dict[word] = word_dict[word] + 1
```

## pickle
- pickling : 구성되어 있는 데이터를 모두 바이너리 형태로 만들어주는 작업
- unpickling
```py
from sklearn.datasets import fetch_20newsgroups

news_sample = fetch_20newsgroups().data
news_samples = news_sample[:30]

import re

news_samples = [re.sub('[^A-Za-z ]', '', news).lower().strip() for news in news_samples]

word_list = []

for news in news_samples:
    word_list += news.split() # list concatenation

from collections import Counter
Counter(word_list)


import pickle

# pickle은 확장자는 ".pk"이며, 쓰기모드는 "wb"로 써야 함
with open("word_list.pk", "wb") as f:
    pickle.dump(word_list, f) # pickling

with open("word_dict.pk", "wb") as f:
    pickle.dump(word_dict, f)


# 바이너리 파일은 열어 볼 수 없음
# 무조건 pickle을 통해 로드해야 함
with open("word_list.pk", "rb") as f:
    word_list2 = pickle.load(f) # unpickling
```

## shutil
- 파일들을 한 번에 복사 또는 이동하는 라이브러리
```py
# 파일을 모두 가져오기 위해 glob() 사용
from glob import glob
img_files = glob("../input/landmark_img/0/0/0/*.jpg")


# 파일 옮기기
import shutil

# for문은 순서대로 돌기 때문에 copy 자체의 순서는 바뀌지 않음
for i, img_file in enumerate(img_files):
    # 꼭 절대경로 사용
    shutil.copy(img_file, f"./{i}.jpg")
    shutil.move(img_file, f"./{i}.jpg")
```

## zipfile
- 압축 파일의 해제 및 생성 라이브러리
```py
import zipfile

img_files = glob("./*.jpg")
len(img_files)

# 압축할 아카이브 파일 생성
with zipfile.ZipFile("./imgs.zip", 'w') as f:
    for img_file in img_files:
        f.write(img_file) # imgs.zip 파일에다가 해당 파일을 archive함

# 압축파일 만들어졌는지 확인
## 성공했을 경우의 출력 : ['./imgs.zip']
glob("./*.zip")

# 헷갈리지 않게 파일 생성
!mkdir test


# extractall() : 특정 경로에 압축이 모두 해제
with zipfile.ZipFile("./imgs.zip", 'r') as f:
    f.extractall("./test/")

glob("./test/*.jpg")
```

## time, calendar
- 현재 시간 출력 또는 코드 실행 시간 측정 등을 하는 라이브러리
- time
    - cpuclockid
    - localtime
    - time.sleep
    - time.time
    ```py
    from time import time

    start = time()

    print("Hello")

    end = time()

    # 걸린 시간 출력
    ## 초 단위로 출력
    print("Elapsed Time: %.4f secs." % (end - start)) 
    
    
    # %%timeit : 실제 시스템에서 얼마나 실행했는지 측정
    ## 보통 시스템 명령을 여러 번 실행하여 의도하지 않은 과부하를 일으킬 수 있음
    %%timeit
    ```
- calendar
    ```py
    from calendar import calendar

    print(calendar(2022))
    ```
    

## SQLite
- 기본적으로 간단하게 DB를 사용할 수 있도록 만들어진 라이브러리
    - DATABASE
        1. Relational : 테이블 형태의 DB
        1. NoSQLite : 비정형 데이터 형태의 DB
- C++, C, Java 등 지원
- `sqlite3` : SQL을 파이썬에서 사용하기 위한 라이브러리, 불러와서 DB에 연결함
    - 커서 : 데이터베이스에서 조회한 결과들을 탐색할 수 있는 객체
```py
import sqlite3

# SQLite DB 연결
conn = sqlite3.connect("../input/module02/univdb-sqlite.db")

# Connection으로부터 Cursor 생성
cur = conn.cursor()

# SQL 쿼리 실행
## 지정된 테이블에 있는 모든 데이터 불러올 것
cur.execute("SELECT * FROM STUDENT")

# 데이터 Fetch
rows = cur.fetchall()

for row in rows:
    print(row)

conn.close()
```
- [DB Browser for SQLite]()