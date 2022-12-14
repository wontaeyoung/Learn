## 리눅스(Linux)

- 1991년 ‘리누스 토발즈'에 의해 오픈소스로 개발된 유닉스 호환 OS
- 이름의 유래는 리누스의 유닉스
- 오픈소스 운영체제로 기존의 리눅스 커널에 다양한 변화가 추가된 배포판들이 있음
    - 리눅스 커널 자체는 무료지만, 다양한 기업들이 배포판을 유료 서비스로 제공하기도 함
    - 유료 리눅스OS는 추가적인 기능, 기술적인 지원 보장 등을 제공함
    - 대표적인 배포판으로는 데비안, 페도라, 레드펫 그리고 이번 미션의 권장 운영체제인 우분투 등이 있음
- 일반적으로 서버용 컴퓨터의 OS로 활용
    - 대표적인 OS인 윈도우와 맥은 마이크로소프트와 애플에서 제공하는 유료 OS지만, 리눅스는 무료로 사용 가능하기 때문

### 설치 방식 (우분투 기준)

1. PC에 우분투 설치
    
    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7b1891aa-c28e-4992-8d6d-c2117c8ad2f2/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220910%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220910T114617Z&X-Amz-Expires=86400&X-Amz-Signature=57e8dccb4da95e12a9c21a2cfc2d012030e68826274a246d99c94802bf9d1733&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)
    
    - 현재 사용중인 PC의 운영체제로써 우분투 설치
    - 듀얼부팅의 번거로움과, PC부품의 우분투 호환성 고려 필요
2. WSL2
    
    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8ef8e9fa-d52c-4a40-a69b-096316f2883c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220910%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220910T114620Z&X-Amz-Expires=86400&X-Amz-Signature=798b9b4db57063a1c5cb918c986c49d09846245801d1eaa62227950195231705&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)
    
    - 윈도우 10에서 제공하는 서브 시스템(Windows Subsystem for Linux)에서 사용
    - MS에서 제공하는 기능으로 리눅스와 100% 동일하지는 않지만, 학습에는 활용할 수 있는 수준으로 호환
3. 가상머신
    
    ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d3355fd9-73aa-47e6-9a8c-bc7268b4bbba/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220910%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220910T114623Z&X-Amz-Expires=86400&X-Amz-Signature=c5a288aee673cfd8eff16d9115f74714809bd17a238c23e64c56bbe2328531a6&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)
    
    - 학습 목적으로 접근성이 좋은 방식
    - 에뮬레이터의 일종으로 소프트웨어인 가상컴퓨터를 통해 OS를 추가적으로 설치하는 방법
    - PC 자원(CPU 코어, RAM, 저장 공간 등)의 일부를 할당받아 사용하여 작동
    - 에뮬레이팅 방식이기 때문에 속도에서 불이익 발생, 하드웨어의 호환 기능을 온전하게 사용할 수 없음
4. 클라우드 컴퓨터
    - 클라우드 컴퓨터 서비스를 이용하는 방식
    - 선택 유저가 가장 많고, 실제 서비스 서버로도 사용 가능할만큼 안정적인 방법
    - MS Azure, Google Cloud Platform, Amazon Web Service 등이 있음
