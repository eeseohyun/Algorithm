## 문제 설명

두 수의 최소공배수(Least Common Multiple)란 입력된 두 수의 배수 중 공통이 되는 가장 작은 숫자를 의미합니다. 예를 들어 2와 7의 최소공배수는 14가 됩니다. 정의를 확장해서, n개의 수의 최소공배수는 n 개의 수들의 배수 중 공통이 되는 가장 작은 숫자가 됩니다. n개의 숫자를 담은 배열 `arr`이 입력되었을 때 이 수들의 최소공배수를 반환하는 함수, solution을 완성해 주세요.

- 제한 사항
  - arr은 길이 1이상, 15이하인 배열입니다.
  - arr의 원소는 100 이하인 자연수입니다.

### 입출력 예시

| arr        | result |
| ---------- | ------ |
| [2,6,8,14] | 168    |
| [1,2,3]    | 6      |

## 풀이

- 최대공약수 gcd를 이용한 풀이
- `lcm(a,b) = |ab| / gcd(a,b)`

```
function solution(arr) {
    function gcd(a,b){
      let c = 0;
      while(b !== 0){
        c = a % b;
        a = b;
        b = c;
      }
      return a;
    }
    function lcm (a, b) {
       let lcm = a * b / gcd(a,b);
       return lcm;
    }
    var answer = arr[0]
    for(let i=1; i<arr.length; i++){
        answer = lcm(answer,arr[i])
    }
    return answer;
}
```

## 다른 풀이

```
function nlcm(num) {
 return num.reduce((a,b) => a*b / gcd(a,b))
}

function gcd(a, b) {
  return a % b ? gcd(b, a%b) : b
}

```
