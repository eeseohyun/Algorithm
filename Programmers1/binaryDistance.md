## 문제 설명

0 이상의 정수 `n`이 주어질 때, `n`의 이진 표현에서 인접한 두 `1` 사이의 가장 긴 거리를 출력하는 함수, solution을 완성해주세요.

예를 들어, `n`이 주어질 때의 결과는 다음과 같습니다.

- 예시

```
n : 5
n의 이진 표현 : 101
결과 : 2

n : 11
n의 이진 표현 : 1011
결과 : 2
```

- 입력 형식
  - `n`은 0 이상 109 이하의 정수입니다.
- 출력 형식

  - `n`의 이진 표현에서 인접한 두 1 사이의 가장 긴 거리를 `int` 형식으로 출력합니다.

## 풀이

- `n`을 이진수로 변환한 후,
  - 현재 자릿수가 1인 경우, 현재까지의 인접한 1 사이의 거리(`current`)를 확인하고, 최대 거리(`max`)와 비교하여 갱신.
  - 현재 자릿수가 `0`인 경우, 인접한 `1` 사이의 거리를 `1`씩 증가.

```
function solution(n) {
    let binary = n.toString(2);
    let max = 0;
    let current = 0;

    for (let digit of binary) {
      if (digit === '1') {
        if (current >  max) {
        max = current;
      }
      current = 0;
    } else {
      current++;
    }
  }

  return max;
}
```
