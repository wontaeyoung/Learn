## 힙의 단편화 해결 - 메모리 배치 알고리즘

> 외부 단편화로 사용가능한 공간이 비연속적으로 배치되어 있을 때, 새로운 메모리를 효율적으로 적재하는 알고리즘
> 

![사용 가능한 공간 중, 어느 공간을 선택하는 것이 가장 효율적인지에 대한 알고리즘](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5924a516-3b2f-4d50-8cfa-275bcf02d17e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220917%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220917T145634Z&X-Amz-Expires=86400&X-Amz-Signature=c10e5e42f1cb420d1a3cae73619f8ce59626c7904a36a011cb585704fc3379b2&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

사용 가능한 공간 중, 어느 공간을 선택하는 것이 가장 효율적인지에 대한 알고리즘

### 배치 알고리즘의 종류

- 사용 가능한 Hole 중에서 하나의 공간을 선택하기 위한 알고리즘
- First-Fit(최초 적합), Best-Fit(최적 적합), Worst-Fit(최악 적합) 세 가지 알고리즘이 존재
    
    ![Process를 A,B,C 중에 어느 공간에 넣을지 선택하는 상황](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/72e23687-b9b9-4cf1-b6b2-9f658635188d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220917%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220917T145637Z&X-Amz-Expires=86400&X-Amz-Signature=f298cd26a8ace566147f1c79c6c020681863367bc1071e4623760904cd558c38&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)
    
    Process를 A,B,C 중에 어느 공간에 넣을지 선택하는 상황
    

**First-Fit**

- 최초로 발견되는 Hole에 배치하는 알고리즘
- 남은 메모리를 순차적으로 탐색하고, 이 프로세스가 할당될 수 있는 공간 중 최초의 공간에 배치
    
    ![First-Fit](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/dac00ae1-42c5-445e-bf9a-b813ea55816a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220917%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220917T145640Z&X-Amz-Expires=86400&X-Amz-Signature=59eb11a182271e1afdcd670fe657e00ff08b3d700d8e887cbf7f4adc451f7d4d&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)
    
    First-Fit
    

**Best-Fit**

- 가장 최적의 Hole에 배치하는 알고리즘
- 남은 메모리를 전부 탐색하고, 이 프로세스가 할당되었을 때, 낭비되는 공간이 가장 적은 공간에 배치
- 단편화가 가장 적게 발생함
    
    ![Best-Fit](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1539aec6-63fb-4c13-ad7c-f29de40c4088/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220917%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220917T145643Z&X-Amz-Expires=86400&X-Amz-Signature=9aa559f59454becceb025802b87681c93514211d3fafabd01adfe4a9ca21e9ab&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)
    
    Best-Fit
    

**Worst-Fit**

- 가장 큰 Hole에 배치하는 알고리즘
- 남은 메모리를 전부 탐색하고, 가장 큰 공간에 배치
- 낭비 공간이 크면, 이후에 해당 공간에 다른 프로세스를 추가적으로 배치할 수 있을 것을 기대하는 방식
    
    ![Worst-Fit](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/78634ffb-37c0-4543-8623-172b50a12044/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220917%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220917T145647Z&X-Amz-Expires=86400&X-Amz-Signature=6a3f3bf948087598877c0c80fbc0ffdb38de31597924a7bb47c9ba5986cd61c8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)
    
    Worst-Fit
