# Regex Pattern

작성자 : gmlwo530
사용 언어 : js

[MDN](https://developer.mozilla.org/ko/)에 있는 [정규 표현식 문서](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/%EC%A0%95%EA%B7%9C%EC%8B%9D)에 있는 내용을 공부해보려 합니다.

이번 문서에서는 정규 표현식을 **만드는 방법**과 정규 표현식의 **패턴**을 공부 했습니다.

## 정규 표현식 만들기

js에서 정규 표현식을 만드는 방법은 2가지가 있습니다.

1. 정규식 리터럴`/`(슬래쉬) 사용

```javascript
var re1 = /ab+c/;

// 만약 정규식이 상수라면 const로 선언하는게 성능을 향상 시킵니다.
const re2 = /ab+c/;
```

2. [`RegExp`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/RegExp) 객체의 생성자 함수 사용

```javascript
var re = new RegExp("ab+c");
```

1번 방법(정규식 리터럴)은 스크립트가 불러와질 때 컴파일 됩니다. 반면, 2번 방법(생성자 함수 사용)은 정규식이 실행 시점에 컴파일 됩니다. 그러므로 정규식의 _패턴이 변경될 수 있는 경우_, 혹은 *사용자 입력과 같이 다른 출처로부터 패턴을 가져와야 하는 경우*에는 생성자 함수를 사용하는게 좋습니다.

## 정규 표현식 패턴

1. 단순 패턴 사용

`abc`라는 패턴이 문자열에 정확히 순서대로 나타나야 대응됩니다.

```javascript
const re = /abc/;

var s1 = "Hi, do you know your abc's?";
s1.split(re); // ["Hi, do you know your ", "'s?"]

var s2 = "Grab crab";
s2.split(re); // ["Grab crab"]
```

2. 특수 문자 사용

검색에서 하나 이상의 특정 문자 또는 공백을 찾는거와 같이 '있는 그대로의 대응' 이상의 대응을 해야 할 경우 특수 문자를 포함한다.

```javascript
const re = /ab*c/; //*는 *의 앞의 문자가 0개 이상이라는 것을 의미

var s = "cbbabbbbcdebc";
s.replace(re, "-"); // "cbb-debc"
```

---

**Reference**

- [https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/%EC%A0%95%EA%B7%9C%EC%8B%9D](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/%EC%A0%95%EA%B7%9C%EC%8B%9D)
