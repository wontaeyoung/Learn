# 힙의 단편화 해결 - 메모리 배치 알고리즘

> 외부 단편화로 사용가능한 공간이 비연속적으로 배치되어 있을 때, 새로운 메모리를 효율적으로 적재하는 알고리즘
> 

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5924a516-3b2f-4d50-8cfa-275bcf02d17e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220917%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220917T145634Z&X-Amz-Expires=86400&X-Amz-Signature=c10e5e42f1cb420d1a3cae73619f8ce59626c7904a36a011cb585704fc3379b2&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width="50%" height="50%">







## 배치 알고리즘의 종류

- 사용 가능한 Hole 중에서 하나의 공간을 선택하기 위한 알고리즘
- First-Fit(최초 적합), Best-Fit(최적 적합), Worst-Fit(최악 적합) 세 가지 알고리즘이 존재

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/72e23687-b9b9-4cf1-b6b2-9f658635188d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220917%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220917T145637Z&X-Amz-Expires=86400&X-Amz-Signature=f298cd26a8ace566147f1c79c6c020681863367bc1071e4623760904cd558c38&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width="50%" height="50%">
    

**First-Fit**

- 최초로 발견되는 Hole에 배치하는 알고리즘
- 남은 메모리를 순차적으로 탐색하고, 이 프로세스가 할당될 수 있는 공간 중 최초의 공간에 배치

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/dac00ae1-42c5-445e-bf9a-b813ea55816a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220917%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220917T145640Z&X-Amz-Expires=86400&X-Amz-Signature=59eb11a182271e1afdcd670fe657e00ff08b3d700d8e887cbf7f4adc451f7d4d&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width="50%" height="50%">
    

**Best-Fit**

- 가장 최적의 Hole에 배치하는 알고리즘
- 남은 메모리를 전부 탐색하고, 이 프로세스가 할당되었을 때, 낭비되는 공간이 가장 적은 공간에 배치
- 단편화가 가장 적게 발생함
    
<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1539aec6-63fb-4c13-ad7c-f29de40c4088/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220917%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220917T145643Z&X-Amz-Expires=86400&X-Amz-Signature=9aa559f59454becceb025802b87681c93514211d3fafabd01adfe4a9ca21e9ab&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width="50%" height="50%">
    

**Worst-Fit**

- 가장 큰 Hole에 배치하는 알고리즘
- 남은 메모리를 전부 탐색하고, 가장 큰 공간에 배치
- 낭비 공간이 크면, 이후에 해당 공간에 다른 프로세스를 추가적으로 배치할 수 있을 것을 기대하는 방식

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/78634ffb-37c0-4543-8623-172b50a12044/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220917%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220917T145647Z&X-Amz-Expires=86400&X-Amz-Signature=6a3f3bf948087598877c0c80fbc0ffdb38de31597924a7bb47c9ba5986cd61c8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width="50%" height="50%">

## 세 알고리즘의 효율성 비교

시뮬레이션 출처 - [링크](http://boron.physics.metu.edu.tr/ozdogan/OperatingSystems/ceng328/node182.html)

1. Worst-Fit이 성능이 가장 좋지 않음 (시간과 스토리지 활용률 감소 측면)
    - 정렬되지 않은 목록에 대해서 전체 탐색이 필요함
    - 남은 공간의 활용성보다 남은 공간을 적게 하는 것이 더 효율적이기 때문
2. 스토리지 활용률 측면에서 First-Fit과 Best-Fit의 성능은 비슷함
3. First-Fit이 시간 측면에서 일반적으로 성능이 더 좋음
    - Best-Fit도 정렬되지 않은 목록에 대해서 전체 탐색이 필요함

### 요약

- 스토리지 활용률
    - First-Fit = Best-Fit > Worst-Fit
- 시간
    - First-Fit > Best-Fit = Worst-Fit
- 종합
    - First-Fit > Best-Fit > Worst-Fit

### 세 알고리즘을 직접 구현해보자

```swift
enum FitAlgorithm : String {
    case firstFit
    case bestFit
    case worstFit
}

func allocToFitSpace(neededSize : Int, Algorithm : FitAlgorithm) -> String {
    
    var chosenIndex : Int = 0 // 선택된 메모리의 index
    var chosenSize : Int = 0 // 선택된 메모리 공간 
    var wastedSize : Int = 0 // 프로세스를 사용하고 낭비된 공간
    
    
    switch Algorithm {
    
    // 필요한 공간 <= 사용 가능한 공간 중 처음으로 true인 공간을 return
    case .firstFit:
    for (idx,value) in usableMemory.enumerated() {
        if neededSize <= value {
            chosenIndex = idx
            chosenSize = value
            wastedSize = value - neededSize
            break
        }
    }
        
    // 사용 가능한 공간을 모두 체크한 뒤, 낭비 공간이 가장 적은 공간을 return
    case .bestFit:

        // 필요 공간보다 큰 공간만 필터 -> 오름차순 정렬 -> 첫 번째 공간
        let fittestSpace = usableMemory.filter{$0 >= neededSize}.sorted()[0]
        
        chosenIndex = usableMemory.firstIndex(of: fittestSpace)!
        chosenSize = fittestSpace
        wastedSize = fittestSpace - neededSize
    
    // 사용 가능한 공간 중 가장 큰 공간을 return 
    case .worstFit:
        let maxSpace = usableMemory.max()!
        
        chosenIndex = usableMemory.firstIndex(of: maxSpace) ?? 0
        chosenSize = maxSpace
        wastedSize = maxSpace - neededSize
    }
    
    
    return "사용 가능한 메모리 공간 : \(usableMemory)\n선택 알고리즘 : \(Algorithm)\n선택된 메모리 index : \(chosenIndex)\n선택된 메모리 공간 : \(chosenSize)\n필요한 공간 : \(neededSize)\n낭비된 공간 : \(wastedSize)"
}

// 사용 가능한 공간 리스트
let usableMemory = [10,50,30,20,70,20,35,25,10]

print(allocToFitSpace(neededSize: 25, Algorithm: .firstFit))
print("---------------------------------------------------")
print(allocToFitSpace(neededSize: 25, Algorithm: .bestFit))
print("---------------------------------------------------")
print(allocToFitSpace(neededSize: 25, Algorithm: .worstFit))
```

### 실행 결과

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6ffc52d8-391d-4e19-b452-a40863d997bf/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220918%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220918T124423Z&X-Amz-Expires=86400&X-Amz-Signature=5b7e041f361a1d53380079a16500dd471d471a5f4dac9a5d0f5c2690c2dc97fd&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width="50%" height="50%">

- First-Fit
    - 필요 공간 25 이상인 2번째 Hole 50에 할당
- Best-Fit
    - 필요 공간 25 이상인 Hole 중, 25와 가장 차이가 적은 8번째 Hole 25에 할당
- Worst-Fit
    - Hole 리스트 중 가장 큰 공간인 5번째 Hole 70에 할당
