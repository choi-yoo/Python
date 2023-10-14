# Python
- 자동으로 data type 결정됨
- indentation(들여쓰기/내어쓰기)을 이용하여 code block 구분
- 문자열 data type이 따로 존재
- inteprinter : line by line 실행

# PyPI : Python Package Index
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

# Kaggle 
- Kaggle
    - 머신러닝 및 데이터 사이언스 커뮤니티
- Kaggle Notebook 
    - 캐글에서 코드를 작성한 문서

- 단축키
    - `Shift + Enter`
        - 실행하고자 하는 부분 커서 놓고 단축키 누름
    - `Shift + Tap`
        - 상세정보를 알아보려는 함수의 () 안에서 해당 단축키 누름
    - `Tab`
        - 자동 완성
    