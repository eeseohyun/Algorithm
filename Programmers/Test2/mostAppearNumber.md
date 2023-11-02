## 문제 설명

숫자로 이루어진 문자열 `s`가 있습니다.

이 문자열에서 가장 많이 등장하는 `0`~`9` 사이의 숫자를 출력하는 프로그램을 구현하세요.

단, 가장 많이 등장하는 수가 여러 개라면, 그중 가장 작은 수를 반환하세요.

- 입력 형식
  - `s`: 숫자로 이루어진 문자열
- 출력 형식
  - 가장 많이 등장하는 수를 정수로 반환
- 제약 사항
  - `0 < s.length <= 100`

### 입출력 예시

1.

```
  입력 : s = "174771177"
  출력 : 7
  설명 : 7이 가장 많이 등장하였으므로 답은 7이다.
```

2.

```
  입력 : s = "552342502"
  출력 : 2
  설명 : 2와 5가 가장 많이 등장하지만, 2가 더 작으므로 2를 반환
```

## 풀이

- 문자열 `s`의 각 문자들을 키로 사용하여 각 문자가 몇 번 등장하는지 저장하는 객체 `charMap` 생성
- 문자 `char`이 `charMap`에 이미 존재하면 `+1`씩 증가시키고 그렇지 않다면 `1`로 설정
- 현재 카운트 값이 이전의 `max`값보다 크면 현재 값으로 갱신하고, `maxChar`을 현재 `char`로 갱신해준다.

```
function solution(s) {
    const charMap = {};
    let max = 0;
    let maxChar = '';

    for(let char of s){
      if(charMap[char]){
        charMap[char]++
      }else {
        charMap[char] = 1;
      }
    }
    for(let char in charMap){
      if(charMap[char] > max){
        max = charMap[char];
        maxChar = char;
      }
    }

    return Number(maxChar);
}
```
