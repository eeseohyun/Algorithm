## 문제 설명

주어진 두 개의 수를 소인수 분해 했을 때 공통된 소수의 집합을 가지고 있는지 판단하는 함수를 작성하세요.

예를 들어 12, 6 은 두 수 모두 2와 3으로만 이루어져 공통된 소수 집합을 가지고 있습니다.
9, 18의 경우 9는 3으로 이루어져 있으며, 18은 2, 3으로 이루어져 있기 때문에 공통 소수 집합이 아닙니다.

- 입력 형식
  - 1 \~ 10000 사이의 정수 `A`, `B`
- 출력 형식
  - 공통된 소수 집합인 경우 1, 아니면 0

## 풀이

- 소수 `i`가 숫자 `n`을 나눌 수 있을 때까지 `n`의 제곱근까지 반복하고, - 남은 `n`이 2 이상인 경우에는 `n`을 소수로 추가
- 추가로 모든 소인수를 오름차순으로 반환
- 그런 다음, 배열 [A, B]의 각 요소에 대해 soinsu 함수를 적용하여 각 숫자의 소인수분해 결과를 얻은 후,
- 결과가 같은지 확인하기 위해, 두 배열을 JSON 형식의 문자열로 변환하고 이 문자열이 동일한지 확인

```
function solution(A, B) {
    const arr = [A,B];
    function soinsu(n) {
        let prime = [];
        for (let i = 2; i <= Math.sqrt(n); i++) {
            while (n % i === 0) {
                prime.push(i);
                n /= i;
            }
        }
        if(n >= 2){
            prime.push(n);
        }
        let ans = Array.from(new Set(prime));
        return ans.sort((a,b) => a - b);
        }
    var result = arr.map((i)=>soinsu(i))
    const a = result[0]
    const b = result[1]
    const equals = (a, b) => JSON.stringify(a) === JSON.stringify(b);
    if(equals(a,b)){
        return 1
    }else{
        return 0
    }

}
```
