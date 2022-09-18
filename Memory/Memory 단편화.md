# 메모리 단편화

- 메모리 공간이 낭비되어 정상적으로 사용할 수 없는 상태
- 동적인 할당과 해제가 반복되면서 발생
- 특히 게임과 같이 동적 할당과 해제가 수시로 일어나는 프로그램은 꼭 해결해야 하는 문제!

## 단편화의 종류

### 내부 단편화(Internal Fragmentation)

- 프로세스가 필요한 양보다 많은 공간을 할당하여 메모리가 낭비되는 것
- 고정된 길이로 메모리를 할당할 때 발생
- 가변 길이로 할당하여도 메모리의 할당과 해제가 반복되면 발생하게 됨
    - 고정 길이보다 작은 데이터가 들어오게 되면 남은 길이가 낭비됨

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/278e21db-51a9-47aa-85b0-d75dd5d199c3/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220916T145549Z&X-Amz-Expires=86400&X-Amz-Signature=1c8eaee093b5d58f514aa4188900565aa81c5cdadccd8b87d966a0f14dadd040&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width="50%" height="50%">


### 외부 단편화(External Fragmentation)

- 잔여 공간은 충분하지만, 남은 공간이 연속적이지 못해서, 새로운 메모리를 할당할 수 없는 것

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/88249d2e-7f82-49b5-b067-15de19645072/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220916T145555Z&X-Amz-Expires=86400&X-Amz-Signature=237f337a15f814e754f46ae5a9f42646aedd9a4939516c11ace516469bbcc778&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width="50%" height="50%">
    

### 외부 **단편화 예시**

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d83f1ead-d55c-4dc2-a3aa-7e09f3ad08b3/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220916T145557Z&X-Amz-Expires=86400&X-Amz-Signature=f0b505b8400411f3fa57d7c1b45767df602ba141650e612cc37f908e25d68ef8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width="50%" height="50%">

- 잔여 공간은 30이고 새로 할당할 메모리는 15지만, 한 번에 15를 할당받을 공간이 없어서 할당할 수 없음

압축 **예시**


<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c4a76c02-bcdd-41e8-8ee0-a0cb365d6478/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220916T145600Z&X-Amz-Expires=86400&X-Amz-Signature=01b7de164171a060dffa5d27135164d79640784853cdf6e2ed118391f75bb812&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width="50%" height="50%">

- 그림처럼 프로세스가 사용하는 공간을 한 쪽으로 옮기면 해결할 수 있지만 작업 효율이 좋지 않아 오버헤드가 발생
    - 오버헤드 : 어떤 작업의 처리에 들어가는 간접적인 시간, 메모리


# Reference

- https://sycho-lego.tistory.com/m/9
