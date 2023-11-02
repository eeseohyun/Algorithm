## 문제 설명

제로베이스 멤버들은 모두 모여서 마피아게임을 하기로 했습니다.

마피아게임의 규칙은 다음과 같습니다. `N`명의 멤버들은 같은 숫자의 카드를 받고, 단 `2`명만 다른 숫자의 카드를 받습니다.

멤버들은 최소 `5`명이 있으며, 매 게임마다 무조건 `2`명의 마피아가 존재합니다.

이때 마피아인 멤버의 인덱스를 찾아서 오름차순으로 출력해 주세요.

예를 들면 주어진 배열 `members`가 [4, 4, 10, 4, 10] 이라고 할 때,

5명의 멤버들 가운데 `10`의 카드를 가진 멤버가 마피아이고 저희가 출력해야 할 결과는 [2, 4]입니다.

- 입력 형식
  - 배열 `members`가 주어집니다.
- 출력 형식
  - 마피아 2명의 인덱스가 담긴 배열을 오름차순으로 반환합니다.
- 제약 사항

  - 배열 `members`에는 최소 `5`개 이상의 원소가 포함되어 있습니다.

  - 배열 `members`의 모든 원소는 양수입니다.

  - 마피아는 항상 `2`명입니다.

## 풀이

- reduce()를 이용해서 각 원소가 몇 번 나왔는지 `mapia`에 객체로 저장
- 값이 2인 키를 찾음 (2번 나온 원소)
- while 루프를 이용해서 이 원소의 모든 인덱스를 반환

```
function solution(members) {
    const mapia = members.reduce((accu, curr) => {
  accu[curr] = (accu[curr] || 0)+1;
  return accu;
    }, {});
    const keys = Object.keys(mapia);
    const key = keys.find((k) => mapia[k] === 2);
    const result = [];
    var idx = members.indexOf(Number(key));
    while (idx != -1) {
        result.push(idx);
        idx = members.indexOf(Number(key), idx + 1);
    }

    return result
}
```
