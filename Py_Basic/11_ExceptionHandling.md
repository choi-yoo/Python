# Debugging
1. print()를 이용한 디버깅
    - [방법1] `is_print` : True는 프린트 실행/ False는 실행X
        ```py
        is_print = False # True, False

        def change_name(name):
            if is_print:
                print("2. ", name)
            name = "Lee"
            if is_print:
                print("3. ", name)
            return name

        name = "Kim"
        if is_print:
            print("1. ", name) 
        name = change_name(name)
        if is_print:
            print("4. ", name)

        # 출력 : 
        # 1. Kim
        # 2. Kim
        # 3. Lee
        # 4. Lee
        ```
    - [방법2] `debug_level` : 레벨에 따른 디버깅 실행
        - 확ㅇ니하고 싶은 내용을 기능 단위로 만듦
        ```py
        # 레벨에 따른 실행
        debug_level = 1 # 1, 2, 3
        def change_name(name):
            if debug_level >= 2:
                print("2. ", name)
            name = "Lee"
            if debug_level >= 2:
                print("3. ", name)
            return name

        name = "Kim"
        if debug_level == 3:
            print("1. ", name) 
        name = change_name(name)
        if debug_level == 3:
            print("4. ", name)
        ```