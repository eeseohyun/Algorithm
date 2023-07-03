## 문제 설명

전 세계의 알파벳들이 기차놀이를 하기 위해서 한 장소에 모였습니다.

뒤죽박죽 같은 스펠링의 알파벳들도 섞여 들어가 있습니다.
여기에서 반복 없이 가장 긴 알파벳 길이를 구하는 함수, solution을 완성해 주세요.

예를 들어, 문자열 `s`가 'abssccbsbsv' 일 때, 반복 없이 가장 긴 알파벳 길이는 `3`입니다.

- 입력 형식
  - `s`: 길이가 1 이상 1,000 이하인 문자열
- 출력 형식
  - 반복 없이 가장 긴 알파벳 길이를 출력합니다.
- 제한 사항
  - 기차놀이에 참가한 알파벳은 중복될 수 있습니다. 반복 없는 가장 긴 문자열을 찾습니다.

## 풀이

- 현재 문자 `char`이 `currentStr`에 이미 있으면, `currentStr`을 `char`가 나오는 인덱스 다음부터 잘라서 재할당
- `char`가 `currentStr`에 없거나, `currentStr`에서 제거되었으면 `char`를 `currentStr`에 추가
- `countMax`를 `currentStr`의 길이와 현재 `countMax` 중에서 더 큰 값으로 갱신

```
function solution(s) {
    let countMax = 0;
    let currentStr = "";

    for(let i=0;i<s.length;i++){
        let char = s.charAt(i)
        let indexOfCurStr = currentStr.indexOf(char);

        if (indexOfCurStr !== -1) {
            currentStr = currentStr.substr(indexOfCurStr + 1);
        }

        currentStr += char;
        countMax = Math.max(countMax, currentStr.length);
    }

    return countMax;
}
```
