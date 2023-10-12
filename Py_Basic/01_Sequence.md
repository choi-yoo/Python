# Sequential Data Types
- 여러 데이터를 하나의 변수에 가지고 있는 자료형
- 크기 제한이 없으나, 메인 메모리 용량 이상일 수 없음
- 종류
    1. List
    1. Tuple
    1. String
- 변경 여부에 따른 분류
    - mutable data type
        1. list
        1. dict
        1. set
    - immutable data type
        - 메모리에 있어 효율적
        1. int
        1. float
        1. string 
        1. tuple
        1. frozenset


## List VS. Dict 예시
- 리스트로 도서 관리하기
    ```py
    name_list = ['python basic', 'Data Base', 'Demian', 'The Alchemist', 'The Prince']
    number_list = ['0011', '123', '3014', '9744', '8861']
    category_list = ['IT', 'IT', 'novel' 'novel', 'humanities']

    print(f"도서명: {name_list[0]}\n도서번호: {number_list[0]}\n도서분류: {category_list[0]}")
    # 출력 
    ## 도서명: python basic
    ## 도서번호: 0011
    ## 도서분류: IT
    ```
- 사전으로 도서 관리하기
    ```py
    # 관리법1
    ## 리스트 3개를 묶어서 사용
    name_list = ['python basic', 'Data Base', 'Demian', 'The Alchemist', 'The Prince']
    number_list = ['0011', '1234', '3014', '9744', '8861']
    category_list = ['IT', 'IT', 'novel' 'novel', 'humanities']

    book_dict1 = {
        'name' : name_list,
        'number' : number_list,
        'category' : category_list
    }

    book_dict1['number'][0] # 출력 : 0011
    ```
    ```py
    # 관리법2
    ## 도서 1권당 하나씩 구성

    book_dict2 = {
        0 : {'name' : 'python basic', 'number' : '0011', 'category' : 'IT'},
        1 : {'name' : 'Data Base', 'number' : '1234', 'category' : 'IT'},
        2 : {'name' : 'Demian', 'number' : '3014', 'category' : 'novel'}, 
        3 : {'name' : 'The Alchemist', 'number' : '9744', 'category' : 'novel'}, 
        4 : {'name' : 'The Prince', 'number' : '8861', 'category' : 'humanities'} 
    }

    book_dict2[0]['name']
    ```