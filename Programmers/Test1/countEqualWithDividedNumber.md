## 문제 설명

크기가 `n`인 숫자 배열 `nums`와 숫자 `d`가 주어집니다. `0 <= a < b < n`과 같다고 할 때, 아래 규칙을 만족하는 `a`, `b` 쌍의 개수를 출력하는 함수, solution을 완성해 주세요.

nums[a] == nums[b] 이면서 nums[a]가 d로 나누어 떨어진다.

예를 들어, `nums`가 [4, 1, 2, 1, 4]이고, d가 2일 때 다음과 같습니다.

- nums[0] == nums[4], 4는 2로 나누어 떨어진다.
- nums[1] == nums[3], 1은 2로 나누어 떨어지지 않는다.

결과는 `1`입니다.

- 입력 형식

  - `nums`는 1 이상 10 이하의 정수로 이루어진 길이가 100 이하의 배열입니다.
  - `d`는 1 이상 10 이하의 정수입니다.

- 출력 형식
  - 규칙을 만족하는 `a`, `b` 쌍의 개수를 출력합니다.

## 풀이

```
function solution(nums, d) {
    var temp = [];
    for(let i=0; i<nums.length;i++){
        for(let j=i+1; j<nums.length; j++){
            if(nums[i]===nums[j] && nums[i]%d===0){
                temp.push(nums[i])
            }
        }
    }
    return temp.length;
}
```