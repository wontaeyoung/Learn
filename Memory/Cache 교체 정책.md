## 캐시

- 미리 데이터나 값을 저장해두는 임시 장소
- 계산이나 접근 없이 데이터를 얻을 수 있기 때문에 성능이 개선됨

## 캐시 교체 정책

- 캐시는 한정된 공간이기 때문에, 필요에 따라 적합한 정책이 필요
- 교체 정책에 따라 장단점이 있으며, 어떤 순서대로 데이터를 삭제하고 추가할지를 결정함

### 캐시 교체 정책의 종류

- First In First Out (FIFO)
    - 가장 먼저 들어온 데이터를 먼저 삭제하는 알고리즘
    - 구현이 간단하지만, 성능이 좋지 않음
        
        ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e82b58d7-43d8-491e-bff5-69daa34f91d7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220918%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220918T145213Z&X-Amz-Expires=86400&X-Amz-Signature=76b769d01846182cdf190566ad45ae1892ea455098fae1703fa28207f60184d0&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)
        

- Optimal Page Replacement(OPR)
    - 이후의 참조를 예상해서 교체를 결정하는 알고리즘
    - 히트 확률은 높지만, 예측이 필요하기 때문에 구현의 현실성이 부족함
        
        ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/bba4fdaf-1424-4989-aec0-d618f7ff7f5d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220918%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220918T145215Z&X-Amz-Expires=86400&X-Amz-Signature=a293d579d35cb670aeb3370e2459baffa71ba16a25c9d858f438ca1da45d9aaf&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)
        

- Least Recently Used(LRU)
    - 가장 오랫동안 사용하지 않은 데이터를 먼저 삭제하는 알고리즘
    - 구현 난이도에 비해 성능이 좋아서 많이 사용되는 알고리즘
        
        ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d9968152-2e54-4c0b-a31d-641d375d79b7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220913%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220913T101617Z&X-Amz-Expires=86400&X-Amz-Signature=ba5e2230d4b5d259bade603f6310693d3b6bd4f5cedad667d507f9b2a6718d3b&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)
        

- Least Frequently Used(LFU)
    - 가장 적게 참조된 데이터를 먼저 삭제하는 알고리즘
    - 참조가 균일하지 않고, 특정 데이터가 집중적으로 참조되었다가 다시 사용하지 않는 경우 메모리가 낭비됨
    - 최다 참조 데이터가 여러 개라면 가장 오랫동안 사용하지 않은 데이터를 삭제
        
        ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2f7a7593-fc9d-4afa-8b8c-1bab20a222e1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220913%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220913T101621Z&X-Amz-Expires=86400&X-Amz-Signature=15de7b8e1bdcf7dd178e0a389d195755dc9c8c4cbab6bcc9b4eac4c4f19efcde&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)
        

- Most Frequently Used(MFU)
    - 가장 많이 참조된 데이터를 먼저 삭제하는 알고리즘
    - 참조가 균일하게 이루어질 때, 이미 많이 사용된 데이터는 이후에 사용되지 않을 것으로 예상하고 삭제
        
        ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c2e796fb-c44c-4d26-ad7c-ede94e56c36d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220913%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220913T101624Z&X-Amz-Expires=86400&X-Amz-Signature=5a57da078440a6c62e1a28e645317ce0e7a786ae50b80a2ab8a884cd67004438&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)
        

> LRU가 구현 난이도에 비해 성능이 좋기 때문에, 상대적으로 구현이 어려운 횟수 기반의 LFU와 MFU는 잘 사용하지 않음
>
