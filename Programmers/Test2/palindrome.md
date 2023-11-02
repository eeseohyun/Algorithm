## 문제 설명

문자열 `S`는 하나의 단어를 나타냅니다.
단어를 거꾸로 뒤집어도 똑같은 것을 회문이라고 합니다.

주어진 단어가 회문인 경우 1, 아닌 경우 0을 리턴하는 함수를 구현하세요.

- 입력 형식
  - `S`: 1000자 미만의 문자열(알파벳 대문자)
- 출력 형식
  - 회문 인경우 `1`
  - 그렇지 않은 경우 `0`

## 풀이

- for문을 뒤에서부터 실행하여 역순으로 재배치해준다.
- 해당 문자열 `S`와 재배치된 문자열이 같은지 비교

```
function solution(S) {
    let tmp = '';
    for(let i = S.length-1;i>=0;i--){
        tmp += S[i];
        for(let j=0; j<tmp.length; j++){
            if(tmp[j] == S[j]){
                return 1
            }else {
                return 0
            }
        }
    }
}
```

- reverse() 이용도 가능

```
function solution(S){
  let reverse = S.split('').reverse().join('');
  return S === reversed ? 1 : 0;
}
```
