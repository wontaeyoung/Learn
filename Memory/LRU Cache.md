# LRU

- 참조한지 오래 되었으면 앞으로도 참조할 가능성이 적을 것이라는 가정으로 사용하는 기법
- 가장 오랫동안 참조하지 않은 데이터를 우선적으로 교체하는 정책
- 이중 연결 리스트, 해시 맵 등으로 구현이 가능

## LRU 설계 (의사코드)

```swift
# 캐시 메모리 리스트는 maxSize가 정해져 있는 리스트
# 데이터 사용은 [키워드 : 데이터]로 이루어진 Dictionary 타입

1 만약에 입력 키가 캐시 메모리에 있으면
	2 키에 해당하는 데이터를 출력
3 없으면
	4 만약에 캐시 메모리가 최대 캐시 사이즈와 같으면
		5 가장 처음 참조된 데이터를 삭제 (head에 가장 가까운 데이터)
	6 새 데이터를 메모리 끝에 추가 (tail에 추가)
```

### Dictionary와 LRU

- LRU는 Doubly Linked List와 Dictionary(Hash Map)로 구현 가능
    - Doubly Linked List
        - 새로운 데이터가 추가될 때 Tail에 추가
        - Head에 가까울수록 사용한 지 오래된 데이터
        - 한정된 공간을 초과하면 Head를 지우고, Tail에 새 데이터를 저장
        - 탐색의 시간복잡도가 O(1)
    - Dictionary
        - key - value로 구성된 자료구조
        - key가 고유하기 때문에, 입력한 key에 대해서 데이터 탐색의 시간복잡도가 O(1)

## 웹 크롤링에 LRU 활용 예시 구현

- 캐시 키워드가 모여있는 배열(Cache List)과, 키워드 - 검색 결과로 이루어진 해시 맵(Cache Dictionary) 이용하여 구현
    1. 검색어를 Cache List에서 탐색
        1. 검색어가 Cache List에 존재하는 경우
            1. 해당 키워드로 Cache Dictionary를 검색하여 결과를 반환
            2. Cache List에서 해당 검색어를 삭제하고, 마지막 index에 추가
        2. 검색어가 Cache List에 존재하지 않는 경우
            1. Cache List에 여유 공간이 있는 경우
                1. 해당 키워드를 Cache List 끝에 추가
                2. Cache 없이 검색 작업을 통해 결과를 반환
                3. 키워드와 검색 결고를 Cache Dictionary에 추가
            2. Cache List에 여유 공간이 없는 경우
                1. Cache List 첫 번째 Index를 제거
                2. 해당 키워드를 Cache List 끝에 추가
                3. Cache 없이 검색 작업을 통해 결과를 반환
                4. 키워드와 검색 결고를 Cache Dictionary에 추가
### 구현 스크립트

```swift
// cache -> [last used, ... , first used]

var cacheList : [String] = [] // LRU 캐시 알고리즘의 키워드가 저장되는 배열

var hitLog : [String : Int] = [:] // 각 키워드의 캐시 히트 횟수

var keyData : [String : [String]] = [:] // 각 키워드의 데이터( 데이터 갯수는 maxDataSize )

// 조건에 따라 캐시 데이터 활용 or 크롤링하여 출력할 텍스트를 반환하는 함수
func cacheController(keyword : String, maxCacheSize : Int, maxDataSize : Int) -> [String] {
    
    // $cache 입력 시, 현재 캐시 리스트에 있는 키워드들의 hitCount를 반환하고 종료
    if keyword == "$cache" {
        
        var hitCounter : [String] = []
        
        // 캐시 리스트에 있는 키워드만 히트 횟수 출력
        for (k,v) in hitLog {
            if cacheList.contains(k) {
                hitCounter.append("\(k)(\(v))")
            }
        }
        guard !hitCounter.isEmpty else { return ["\n저장된 키워드가 없습니다."]}
        return hitCounter
    }
    
    // 캐시 리스트에 입력 키워드가 있는 경우
    else if cacheList.contains(keyword) {
        
        hitLog[keyword]! += 1 // 해당 키워드의 hitCount 1 증가
        
        // 사용된 키워드를 끝자리로 이동
        cacheList.remove(at: cacheList.firstIndex(of: keyword)!)
        cacheList.append(keyword)
        
        print("\n(본 검색 결과는 캐시에 저장된 내용을 표시합니다.)\n")
        
        return keyData[keyword] ?? [] // 캐시 키워드의 데이터를 반환하고 종료
    }
    
    // 캐시 리스트에 입력 키워드가 없는 경우
    else {
        // 캐시 사이즈가 최대인 경우
        if cacheList.count >= maxCacheSize {
            // 가장 오래된 키워드를 캐시 리스트에서 삭제하고, 데이터와 hitCount를 삭제
            keyData[cacheList.first ?? ""] = nil
            hitLog[cacheList.removeFirst()] = nil
        }
        
        let crawlResult : [String] = crawler(keyword: keyword) // 크롤링 결과 리스트
        
        guard crawlResult.count > 0 else { return [] } // 검색 결과가 없으면 캐시 추가 작업을 하지 않고 종료
        
        // hitLog와 keyData에 해당 키워드의 초기 key-value 생성
        hitLog[keyword] = 1
        keyData[keyword] = []
        
        cacheList.append(keyword) // 입력받은 키워드를 끝자리에 추가
                
        // 크롤링 결과와 데이터 사이즈 제한 중 더 작은 범위까지 캐시 데이터에 저장
        for i in 0..<min(maxDataSize,crawlResult.count) {
            keyData[keyword]?.append(crawlResult[i])
        }
        return crawlResult
    }
}
```
