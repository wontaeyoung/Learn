## Git

> Linux의 창시자 ‘리누스 토르발스'가 개발한 분산형 버전 관리 시스템 (DVCS : Distributed Version Control Systems)
> 

### Git의 역사

- Linux 커널이라는 굉장히 큰 오픈소스 프로젝트에서 Patch와 단순 압축 파일로만 버전을 관리하고 있었음
- 2002년에 BitKeeper라는 상용 DVCS를 사용
- 2005년에 BitKeeper에서 유료 전환
- 리누스 토르발스와 Linux 개발 커뮤니티에서 자체 도구를 개발하기로 함
- Git의 특징 및 목표
    - 빠른 속도
    - 단순한 구조
    - 비선형적인 개발(브랜치)
    - 완벽한 분산
    - 대형 프로젝트에서도 활용할 수 있는 수준(속도, 데이터)

### Git의 특징

1. 파일의 저장 방식
    - Git은 데이터를 일련의 스냅샷으로 저장
    - 커밋 시점에 파일들의 상태에 초점을 맞춤
    - 프로젝트 내에서 변화가 없는 파일은 새로 저장하지 않고 링크만 저장
        
        ![시간순으로 프로젝트의 스냅샷을 저장](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0ca423f4-852e-463d-b217-de9920e0c26a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220908T144445Z&X-Amz-Expires=86400&X-Amz-Signature=3ef1d856f7e12e9f65db8bac906e394cee06ab53645f031955a246097d7f3282&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)
        
        시간순으로 프로젝트의 스냅샷을 저장
        

1. 로컬에서의 명령 실행
    - 거의 모든 명령이 로컬 파일과 데이터만 사용
    - 네트워크를 거치지 않기 때문에 속도가 굉장히 빠름
    - 히스토리 관리를 로컬에서 할 수 있기 때문에, 네트워크 혹은 서버에 문제가 발생해도 작업을 진행할 수 있음
    (심지어 비행기 타고 가는 도중에도 할 수 있다고 함 ㅎ…)

1. 파일의 상태
    - Git이 파일을 분류하고 관리하기 위한 상태
    - Modified, Staged, Committed
        - Modified - 수정한 파일을 아직 데이터베이스에 적용하지 않은 상태
        - Staged - 수정한 파일을 곧 적용할 예정임을 표시한 상태
        - Committed - 수정한 파일이 데이터베이스에 안전하게 저장되고 히스토리에 기록된 상태
        
2. 파일의 단계
    - 위의 상태와 연결된 파일의 단계
    - Working Directory, Staging Area, .git directory(Repository)
        - Working Directory - 파일을 수정하는 작업 공간, Modified 상태의 파일이 이 단계에 있음
        - Staging Area - 파일이 커밋되기 전에 머무르는 단계, Staged 상태의 파일이 이 단계에 있음
        - Git directory
            - Git의 핵심으로 프로젝트의 메타데이터와 객체 데이터베이스를 저장하는 곳
            - 다른 클라이언트 혹은 서버의 저장소를 **Clone** 할 때 만들어짐
            - Committed된 파일이 이 단계에 있음
            
            ![Git 파일의 상태와 단계 흐름](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2f0818f3-85e3-405e-aca2-f69b322ef068/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220908%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220908T144502Z&X-Amz-Expires=86400&X-Amz-Signature=0f455b1122f689d616d81896c8dd5fa1f45dd3d59ece53016e342b2195b79d98&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)
            
            Git 파일의 상태와 단계 흐름
