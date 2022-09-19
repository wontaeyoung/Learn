# ARC 

> 하단의 ARC와 관련된 예제 및 이미지는 ‘개발자 소들이'님의 [포스트](https://babbab2.tistory.com/26?category=831129)에서 출처하였습니다.
>

## 참조 타입과 Heap

- 인스턴스, 클로저 등 참조 타입(Reference Type)은 자동으로 힙에 할당
- 지역 변수에 Human 클래스의 인스턴스를 생성하고 값을 초기화하는 경우 메모리에 아래와 같이 할당

    
<img width="493" alt="image" src="https://user-images.githubusercontent.com/45925685/191023056-327d1ed8-0f79-4337-bc60-ba6dbbfaf5f8.png">

    
- 각 속성을 포함하고 있는 Human 클래스의 실제 인스턴스는 힙에 할당
- 지역변수는 스택에 할당되고, 힙에 있는 인스턴스를 참조 → 인스턴스의 주소값을 가지고 있음
- 새로운 지역 변수에 기존 지역 변수를 할당하면 인스턴스가 복사되지 않고, 같은 인스턴스를 참조함
    
<img width="488" alt="image" src="https://user-images.githubusercontent.com/45925685/191024734-3ce97217-348b-4c8d-bb64-f5b9489fedca.png">

    
- 힙의 특징으로 사용하고 난 메모리는 반드시 직접 해제해야하지만, 실제로 인스턴스를 직접 메모리에서 해제한 적은 없음
    - 직접 해제하지 않으면, 함수가 종료되서 지역 변수들이 해제되었을 때 아래와 같은 상태가 됨
        
<img width="480" alt="image" src="https://user-images.githubusercontent.com/45925685/191024767-bba560cf-6b23-4f04-9635-9be3e06a36b3.png">
        
- ‘ARC’가 이러한 메모리 누수를 해결하기 위해 작동함

## ARC

- 클래스 인스턴스가 더 이상 필요하지 않을 때 메모리를 자동으로 해제해주는 기능
- 이론상 힙의 메모리는 할당과 해제를 직접 해주어야하지만, 사용이 끝난 메모리를 직접 해제해주지 않아도 ARC가 이를 대신 수행해줌

## GC와 RC

- 힙 영역의 메모리를 관리하는 대표적인 두 방법
- 자바의 GC(Garbage Collection)이 유명함
- 스위프트의 ARC는 RC에 포함됨

### GC의 특징
  - 참조 계산 시점
      - Run Time
      - 앱 실행 동안 주기적으로 참조를 추적하여 사용하지 않은 인스턴스를 해제
  - 장점
      - 인스턴스가 해제될 확률이 RC에 비해 높음
  - 단점
      - 개발자가 참조 해제 시점을 파악할 수 없음
      - Run Time동안 추적 기능을 수행하는 추가 리소스가 필요하여, 성능이 저하될 수 있음

### RC의 특징
  - 참조 계산 시점
      - Compile Time
          - 컴파일 시점에 언제 참조되고 해제되는지 결정 → 런타임에 결정된대로 실행됨
      - 장점
          - 개발자가 참조 해제 시점을 파악할 수 있음
          - Run Time에 추가 리소스가 발생하지 않음
      - 단점
          - 순환 참조가 발생하면 영구적으로 메모리가 해제되지 않을 수 있음

## MRC와 ARC

- Manual과 Automatic의 차이
- MRC
    - 힙에 메모리를 직접 할당,해제 해주는 것
    - 2011년 이전의 Objective-C가 사용한 방법
        - 2011년 이후에는 Objective-C도 ARC 사용

## ARC의 메모리 관리 방법

- 메모리의 참조 횟수(Reference Count 이하 RC)를 계산
- 참조 횟수가 0이 되면 더 이상 사용하지 않는 메모리로 간주하여 해제
    - 특정 인스턴스를 현재 어느 지역 변수가 참조하는지를 카운트하는 것
    - 따라서 모든 인스턴스는 자신의 RC 값을 가지고 있으며, 생성될 때 힙에 같이 저장됨

### RC가 +1 될 때

- RC가 +1이 되는 순간은 인스턴스의 주소값을 변수에 할당할 때
    - 해당 힙 영역의 주소값을 가지는 스택이 늘어날 때마다
- 이 경우는 크게 두 가지 경우
    1. 인스턴스를 새로 생성할 때
        
    <img width="480" alt="image" src="https://user-images.githubusercontent.com/45925685/191024841-980dd1b0-90d2-48a2-b5d2-e6cfe447b4b6.png">

    2. 기존 인스턴스를 다른 변수에 대입할 때
        
    <img width="479" alt="image" src="https://user-images.githubusercontent.com/45925685/191024954-63c0a055-e197-44af-9533-b27818a83e01.png">

        

### RC가 -1이 될 때

- 기본적으로 힙의 인스턴스를 주소값으로 가지던 스택이 사라지는 경우 RC는 -1이 됨
- 크게 네 가지 경우
    1. 인스턴스를 가리키는 변수가 메모리에서 해제되었을 때
        - 변수 sodeul이 생성될 때 RC = 1
        - makeClone 함수가 호출되어 변수 clone이 생성될 때 RC += 1
        - makeClone 함수가 종료되어 clone이 스택에서 해제될 때 RC -= 1
            
            <img width="623" alt="image" src="https://user-images.githubusercontent.com/45925685/191025018-47481f8e-6fb0-44cf-94a0-a35eae16a089.png">

            
        - makeClone이 실행될 때 메모리 예시
            
            <img width="621" alt="image" src="https://user-images.githubusercontent.com/45925685/191025063-342f3907-7842-4c2e-b1a7-4df2c1c8b61e.png">

            
        - makeClone이 종료되어, 스택의 clone이 해제될 때 메모리 예시
            
            <img width="619" alt="image" src="https://user-images.githubusercontent.com/45925685/191025106-4701a9ac-31a0-4dde-b00b-e3de0dc83a1c.png">

            
            
    2. 인스턴스 변수에 nil이 지정되었을 때
        - 변수가 옵셔널 타입인 경우
            - sodeul = Human, clone = sodeul까지 총 2개의 변수가 인스턴스를 참조하므로 RC = 2
            - 옵셔널 타입인 sodeul과 clone에 nil을 할당하면, 참조하던 주소값이 없어져서 RC = 0
        
        <img width="650" alt="image" src="https://user-images.githubusercontent.com/45925685/191025152-92b4905f-d343-4265-bc3d-cd07437227d6.png">

        
    3. 변수에 다른 인스턴스를 할당한 경우
        - sodeul과 clone에 각각 서로 다른 인스턴스를 생성 (각 인스턴스의 RC = 1)
        - sodeul에 clone을 할당하면서 기존의 sodeul에 할당되어있던 인스턴스의 주소값이 사라짐
        - sodeul 인스턴스의 RC = 0, clone 인스턴스의 RC = 2
            
            <img width="621" alt="image" src="https://user-images.githubusercontent.com/45925685/191025196-8800c5f8-49b9-4886-a3f2-2749187cce6e.png">

            
    4. 인스턴스가 다른 클래스에 프로퍼티로 속해있고, 그 클래스의 인스턴스가 메모리에서 해제될 때
        
        <img width="653" alt="image" src="https://user-images.githubusercontent.com/45925685/191025258-b4bf9c23-4f5e-4095-888b-f09c7b243c98.png">

        
        
        - Contacts 클래스는 Human 클래스의 프로퍼티로 속해 있음
        - Human 인스턴스 sodeul을 생성하면, 동시에 프로퍼티인 Contacts 인스턴스 contacts가 생성
            - 두 인스턴스의 RC가 각각 1씩 증가함
            - 메모리 예시
                
                <img width="596" alt="image" src="https://user-images.githubusercontent.com/45925685/191025309-2314f71e-3eeb-48ca-8d3a-a5ed3d10c15a.png">

                
                
        - sodeul에 nil을 할당한 순간, sodeul의 주소값이 사라지면서 Human 인스턴스의 RC가 1 감소함
            
            <img width="621" alt="image" src="https://user-images.githubusercontent.com/45925685/191025363-4ecbcade-c781-4cf2-bae3-543116dc55f0.png">

            
        - Human 인스턴스의 RC가 0이 되면서 ARC에 의해 메모리에서 해제됨
            - 이 때 Contacts 인스턴스의 주소값을 가지고 있는 contacts 프로퍼티도 같이 메모리에서 해제
            - Contacts 인스턴스의 RC가 1 감소함
                
                <img width="596" alt="image" src="https://user-images.githubusercontent.com/45925685/191025432-da5e6cb4-d22d-4b10-a2ad-3f76b2ae9208.png">

                
        - Contacts 인스턴스의 RC가 0이 되어 ARC에 의해 메모리에서 해제
            
            <img width="623" alt="image" src="https://user-images.githubusercontent.com/45925685/191025468-c5d58d47-0c1c-4dd5-b806-078678c1c15d.png">

            
        - 유의할 점으로 Human 인스턴스가 해제되면서, 꼭 Contacts 인스턴스가 메모리에서 같이 해제되는 것은 아님
            - Human 인스턴스의 해제는 Contacts 인스턴스의 RC를 1 감소시킴
            - 이 RC의 감소로 Contacts의 RC가 0이 된다면 Contacts 인스턴스도 메모리에서 해제되지만, Contacts 인스턴스의 RC가 1 이상이라면 아직 메모리에서 해제는 되지 않음


# Reference

- https://babbab2.tistory.com/26?category=831129
