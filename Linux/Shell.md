## 쉘(Shell)

- 운영체제(커널)와의 대화(상호작용) 기능을 지원하는 프로그램
    - 사용자의 명령을 입력받고, 처리 결과를 표시해주기 때문에 대화라고 할 수 있음
- 명령 줄 형태인 CLI(Command Line Interface)와 그래픽 형태인 GUI(Graphic User Interface)가 있음
- 유닉스, 리눅스의 명령어 처리 프로그램의 이름이기도 함
- 쉘은 다양한 종류가 있고, 명령어나 사용법에 대해서 전체적으로는 비슷하며, 세세한 부분에서 차이가 있음
    - 하나의 쉘 사용법을 배우면, 다른 쉘의 사용법을 익히는데 크게 어렵지 않음

### 쉘의 종류

- 본 쉘(Bourne Shell)
    - 벨 연구소의 스티븐 본이 개발한 최초의 쉘
- Bash(Bourne Again Shell)
    - 사용자 친화적이지 않은 본 쉘을 개선하여 사용자 친화적으로 개선한 쉘
    - 주요 리눅스 시스템들의 기본 쉘로 사용되고 있음
    - 윈도우의 리눅스 서브시스템의 모든 프로그램이 Bash를 거쳐서 작동
- Zsh
    - Bash에 비해 더 많은 기능이 탑재. 리눅스를 메인으로 사용하는 경우에 많이 사용 (보통 oh-my-zsh와 함께 사용)
    - Mac OS의 Catalina 버전부터 기본 쉘이 Bash → Zsh로 변경
- 이외에 C쉘, 콘쉘 등 다양한 쉘 종류가 존재
- 현재는 Bash, Zsh를 주로 사용

### 쉘 명령어

**표시 명령어**

- 현재 위치한 디렉토리의 절대 경로 표시
    
    ```bash
    **$ pwd**
    ```
    
- 현재 위치한 디렉토리의 파일/디렉토리 리스트 표시
    
    ```bash
    **$ ls** 
    ```
    
    - **ls의 추가 명령어 $ ls -?**
        
        ```bash
        -a 숨긴파일을 포함한 모든 항목 표시
        -d 디렉토리 정보만 표시
        *-F 디렉토리는 /, 실행가능 파일은 , 소켓파일은 =, 링크인 경우 @를 파일이음 뒤에 표시
        -l 각 항목의 상세 정보들을 함께 표시
        -m 각 항목들을 쉼표로 구분하여 표시
        -r 항목들을 역순으로 표시
        -R 하위 디렉토리의 내용들도 표시
        -s kb 단위로 표시
        -t 최종 수정시간을 기준으로 표시
        -u 최종 액세스 시간 기준으로 표시
        ```
        

**경로 / 디렉토리 / 파일 명령어**

- 해당 경로로 이동
    - 경로에는 .(현재 위치) ..(상위 디렉토리) -(마지막 위치) ~(유저의 최상위 폴더) 등도 활용할 수 있음
    
    ```bash
    $ cd [경로]
    ```
    
- 디렉토리명으로 폴더 생성
    
    ```bash
    $ mkdir [디렉토리명]
    ```
    
- 하위 디렉토리를 연속으로 생성
    
    ```bash
    $ mkdir -p [디렉토리명]/[디렉토리명]/[디렉토리명]
    ```
    
- 파일이나 디렉토리를 복사
    
    ```bash
    $ cp (-r) [복사할 대상] [붙여넣을 경로 또는 새 파일명] 
    ```
    
- 파일이나 디렉토리를 옮기거나 이름을 변경
    
    ```bash
    $ mv [옮길 대상] [대상 디렉토리 또는 새 파일명]
    ```
    
- 대상을 삭제, -r은 디렉토리 삭제 시(하위 파일까지 모두 삭제)
    
    ```bash
    $ rm (-r) [삭제할 대상]
    ```
    
- 관리자 권한으로 명령어 실행
    
    ```bash
    $ sudo ~
    ```
    
- [경로]와 그 하위 디렉토리에서 파일명에 해당하는 파일을 찾아서 표시. "*.txt" 처럼 정규식 사용 가능
    
    ```bash
    $ find [경로] -name [파일명]
    ```
    
- 파일명에 해당하는 파일을 생성
    
    ```bash
    $ touch [파일명]
    ```
    
- 해당하는 파일 (없다면 생성)에 텍스트 추가 >(덮어씌우기) >>(추가하기)
    
    ```bash
    $ echo "텍스트" > [파일명]
    ```
    
- 해당하는 파일의 내용을 표시
    
    ```bash
    $ cat [파일명]
    ```
    
- 해당하는 파일 중 키워드를 포함하고 있는 파일의 파일명과 텍스트 출력
    - -n (키워드가 포함된 라인 번호 출력)
    - -i (대소문자 구별 없이 검색)
    - 파일명에 .만 사용하면 현재 디렉토리와 그 하위 디렉토리에서 검색
    
    ```bash
    $ grep (-n,-i) "키워드" [파일명]
    ```
    
- 환경 변수(전역에서 사용 가능)를 선언하고 값을 할당
    
    ```bash
    $ export [변수명(보통 대문자)]=값
    ```
    
- 선언한 변수를 사용할 수 있음
    
    ```bash
    $ $[변수명]
    ```
    
- 환경 변수 해제
    
    ```bash
    $ unset 변수명
    ```
    
- 텍스트 파일을 필터링하여 행과 열로 출력. $0은 레코드, $1~9는 컬럼 넘버
    
    ```bash
    $ awk '{ print $? }'
    ```

### 디렉토리와 파일 권한 설정

파일 접근 권한

- drwxrwxrwx 의 형태로 표시
- d | rwx | rwx | rwx → file type | Owner | Group | Other
    - File Type
        - - : file
        - d : directory
        - l : symbolic link
        - p :  named pipe
        - c : character device
        - b : block device
    - Owner, Group, Other
        - 파일의 사용자 유형을 세 종류로 나눈 것
        - Owner (u) : 파일의 소유자
        - Group (g) : 파일의 소유 그룹
        - Other (o) : 그 외 모든 사용자
    - rwx
        - 파일에 대한 권한 유형을 세 종류로 나눈 것
        - r : 읽기(Read)
        - w : 쓰기(Write)
        - x : 실행(Execute)
- `$ ls -l [파일명]` 명령어를 통해 파일의 권한 상태를 확인할 수 있음
    
    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d1511b55-0498-4779-94e0-900746dfacd9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220911%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220911T082829Z&X-Amz-Expires=86400&X-Amz-Signature=e86bc1a2518a6d565fbf32408bd9e8a17f5c012cc2871e6014ca6e8f2842858d&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)
    
- `$ chmod [권한] [파일명]` 명령어를 통해 파일의 접근 권한을 변경할 수 있음
    - 8진수로 권한을 입력하는 방법


## 쉘 스크립트(Shell Script)

- 유닉스 계열 운영체제의 많은 쉘들이 사용하는 스크립트
    - 스크립트 언어는 프로그래밍 언어와 유사함
    - 컴파일 되지 않고, 인터프리터(한줄 씩 해석) 방식으로 실행
    - 다른 인터프리터 언어는 인터프리터를 따로 설치해야하지만 (파이썬처럼), 쉘 스크립트는 인터프리터가 쉘 자체에 내장되어 있음
- 따로 프로그래밍 언어로 분류되지는 않지만, 기능적으로는 비슷함
    - 변수 및 기타 자료구조
    - 서브루틴
    - 프로그램 흐름 통제
    - 주석 처리
- 운영체제에 대한 명령, 응용프로그램 실행 등 많은 작업을 자동화하는데 활용할 수 있음
    - 각 프로그램들을 조합하여 자동화하기 어려운 GUI에 비해 CLI가 가진 장점
- 유닉스 계열은 확장자에 대한 구분이 엄격하지 않지만, 일반적으로 쉘 스크립트 파일은 .sh 확장자를 사용함

### 쉘 스크립트의 주 활용

- 주로 반복되는 작업의 자동화를 위해 스크립트 형태로 만들어서 활용
    - 매일 반복적인 크롤링 작업
    - 데이터 백업
    - 알림 작업
    - 서비스 배포
- 파일과 디렉토리, 설정에 대한 권한 확인 및 처리

### 쉘 스크립팅

기본

- 에디터로 스크립트를 작성할 때, 첫 줄은 #!/bin/bash(사용 중인 쉘)을 작성 후 시작
    - **하단의 스크립트는 bash로 돌린다는 의미**

IF 예제

- **cnt 1,2,3 디렉토리를 순차적으로 없으면 만들고, cnt3이 있으면 a.log에 텍스트를 출력한뒤 cnt 디렉토리 3개를 모두 삭제하기**

```bash
#!/bin/bash
    if ! [ -d cnt1 ]
    then
        mkdir cnt1
    elif ! [ -d cnt2 ]
    then
        mkdir cnt2
    elif ! [ -d cnt3 ]
    then
        mkdir cnt3
    else
        cat a.log
        rm -rf cnt*
    fi
```

FOR **예제**

- **script 파일을 실행하고 현재 디렉토리의 리스트를 보여주는 동작을 10회 반복**

```bash
#!/bin/bash

    for i in {1..10}
    do
        ./script
        ls
    done
```

# Reference

[https://spookyjelly.tistory.com/33](https://spookyjelly.tistory.com/33)

[https://namu.wiki/w/Linux?from=리눅스](https://namu.wiki/w/Linux?from=%EB%A6%AC%EB%88%85%EC%8A%A4)

[https://nemomemo.tistory.com/48](https://nemomemo.tistory.com/48)

[https://ko.wikipedia.org/wiki/셸](https://ko.wikipedia.org/wiki/%EC%85%B8)

[쉘 스크립트](https://engineer-mole.tistory.com/200)
