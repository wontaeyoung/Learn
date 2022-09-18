## 프로세스 메모리 구조 모델

![High Address.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/4354a87a-feb8-4efb-a67d-a794ae2fdb8c/High_Address.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220916T142149Z&X-Amz-Expires=86400&X-Amz-Signature=df804045220d7c7d8b821488808b39637779343274c30152da7ba4c70c79bed3&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22High%2520Address.png%22&x-id=GetObject)

### 코드 영역

- Text
    - 함수코드, 제어문, 상수 등 기본적인 소스 파일 텍스트가 기계어 형태로 저장되는 영역
    - 컴파일 때 결정, 중간에 코드가 변경되지 않도록 Read-Only 형태로 저장
    - CPU에서 해당 영역에 접근하여 저장된 명령어를 하나씩 가져가서 처리

### 데이터 영역

- 전역 변수와 정적 변수가 저장되는 영역
- 프로그램이 시작할 때 생성, 종료되면 해제
- 범위기 정해지지 않은 전역(Global or Static) 변수를 포함
- 실행 도중 변수 값이 변경될 수 있으니, Read-Write 형태로 저장
- GVAR(Global Variable)
    - 초기 값이 0이 아닌 전역 변수(직접 0이 아닌 특정 값을 할당한 변수)
- BSS
    - 초기화 안한 전역 변수

### 힙 (낮은 주소값부터 할당)

- 프로그래머가 할당, 해제하는 메모리 영역 (동적으로 할당하는 메모리 공간)
- malloc이나 new 명령으로 할당
- 사용하고 난 후에는 반드시 메모리 해제를 해줘야 함
    - 해제하지 않으면 Memory Leak이 발생함
- 다른 영역과 다르게 런타임 때 결정되기 때문에, 데이터의 크기가 확실하지 않은 경우 사용
- 클래스의 인스턴스, 클로저와 같은 참조 타입이 모두 힙에 할당됨
- 장점
    - 메모리 크기에 제한이 없음
    - 본질적으로 전역 범위 → 프로그램의 모든 함수에서 액세스할 수 있음
- 단점
    - 할당 - 해제 작업으로 인한 속도 저하
    - 힙 손상(이중 해제, 해제 후 사용)으로 인한 속도 저하
    - 힙 경합(두 개 이상의 스레드가 동시 접근하여 걸리는 Lock)으로 인한 속도 저하
    - 메모리를 직접 관리해야함(해제해주지 않으면 메모리 누수(leak) 발생)
- 힙 영역에 할당한 메모리 공간에 대해 주소를 참조하는 경우가 많음 (CS50, malloc, 포인터)
    
    ![var myAge.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e18a6ca5-a741-422e-8061-180ff15e8423/var_myAge.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220916T142909Z&X-Amz-Expires=86400&X-Amz-Signature=14c48fae501cd551093c532b2e78617973f6019873bf1a2df0ca088af84a7103&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22var%2520myAge.png%22&x-id=GetObject)
    

### 스택 (높은 주소값부터 할당 )

- 함수의 지역변수, 매개변수가 저장되는 영역
- 함수가 호출되면 할당 → 종료되면 해제
- 컴파일 때 결정 → 무한히 할당할 수 없음
- 장점
    - CPU가 스택 메모리를 효율적으로 구성 → 속도가 매우 빠름
    - 메모리를 직접 해제해주지 않아도 됨
- 단점
    - 메모리 크기에 대한 제한
    - 지역 변수에만 액세스 가능
- 스택에 너무 많은 메모리를 할당하면 ‘스택 오버플로우'가 발생
    - 스택에 너무 많은 메모리를 할당 → 자신의 스택 영역을 초과한 경우
    - 종료 시점이 정해지지 않은 무한 재귀 호출 실행 시 확인할 수 있음
    - iOS에서 스택 오버플로우 발생 시, 앱이 강제로 종료됨
- 스택 영역은 ‘스택(Stack) 구조’로 되어있음
    - 나중에 생성된 데이터가 먼저 해제 (LIFO)
    - push로 데이터를 저장, pop을 통해 제일 상단에 있는 데이터를 꺼냄
    
    ![Pasted Graphic.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a35d6c1e-93f7-445e-87e5-f5341ed0fba2/Pasted_Graphic.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220916T142930Z&X-Amz-Expires=86400&X-Amz-Signature=9f44e2131a3fc7e4eb8da0a2f6fd1d7418962c97d1200ddee0c7d13278b80a0c&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Pasted%2520Graphic.png%22&x-id=GetObject)
    

### 힙과 스택의 관계

- 힙과 스택은 개별적인 특징을 가지고 있지만, 같은 메모리 공간을 공유함
    - 한정된 메모리 공간의 양 끝에서, 사용하는만큼 중앙점에 가까워지는 형태
    - 힙은 낮은 메모리 주소부터, 스택은 높은 메모리 주소부터 사용함
    
    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6afd39a4-7820-423f-969e-a7e432c085a2/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220916T142949Z&X-Amz-Expires=86400&X-Amz-Signature=f26ab1dabc5150780cb709f7b3bf8cec43d7558aa78fcef30a396bd959aa4d5a&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)
    

## iOS의 가상 메모리

- 메모리 관리는 좋은 사용자 경험을 제공하기 위한 중요한 요소
- 메모리는 한정된 자원이며, 여러 프로세스가 공유하는 자원
    - 메모리 누수로 인해 현재 앱이 차지하는 메모리가 커지게 되면, 백그라운드의 다른 앱을 강제 종료시키거나, 현재 앱이 강제 종료될 수 있음
- 메모리 릭이 일어나는지 알아내고 해결하는 과정이 매우 중요
- iOS 메모리 관리에 대한 세부 내용 - [링크](https://seizze.github.io/2019/12/20/iOS-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EB%9C%AF%EC%96%B4%EB%B3%B4%EA%B8%B0,-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%9D%B4%EC%8A%88-%EB%94%94%EB%B2%84%EA%B9%85%ED%95%98%EA%B8%B0,-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EB%A6%AD-%EC%B0%BE%EA%B8%B0.html)

# Reference

- https://www.jiwon.me/explain-heap-and-stack/
- https://seizze.github.io/2019/12/20/iOS-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EB%9C%AF%EC%96%B4%EB%B3%B4%EA%B8%B0,-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%9D%B4%EC%8A%88-%EB%94%94%EB%B2%84%EA%B9%85%ED%95%98%EA%B8%B0,-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EB%A6%AD-%EC%B0%BE%EA%B8%B0.html
- https://babbab2.tistory.com/25
