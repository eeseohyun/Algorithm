## 문제 설명

문자열 `s`가 주어집니다. `s`가 pangram 인지 판단하는 함수, solution을 완성해주세요.

pangram이란 모든 알파벳이 사용된 문장을 말합니다.

- 입력 형식
  - `s`: 길이가 1 이상 1,000 이하인 문자열, 소문자 알파벳과 공백(' ')으로만 구성
- 출력 형식
  - 문자열이 pangram인지 구합니다.
  - 문자열이 pangram이면 `true` 그렇지 않으면 `false`를 출력합니다.

## 풀이

- `replace` 메서드와 `정규 표현식`을 사용하여 소문자 알파벳을 제외한 모든 문자를 빈 문자열로 대체

- 제거 작업을 거친 문자열을 `Set`으로 변환하여 중복된 문자를 제거합

- Set 객체를 다시 배열로 변환

- 배열의 길이가 26인지 확인. 배열의 길이가 26이면 입력 문자열 `s`는 모든 알파벳을 포함하고 있는 것이므로 팬그램이므로 `true` 반환, 아니면 `false` 반환

```
function solution(s) {
    let str = s.replace(/[^a-z]/g,'')
    const toArr = [...new Set(str)]
    return toArr.length === 26 ? true : false
}
```
