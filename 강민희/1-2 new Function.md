# new Function

new Function은 왜 쓰는걸까?? 🤔

<br>

### [ new Function 사용법 ]

```js
let add = new Function("a", "b", "return a + b");

console.log(add(1, 2)); // 3
```

```js
// 인수가 없는 경우
let sayHi = new Function('alert("Hello")');

sayHi(); // Hello
```

기존에 사용하던 방법과`new Function을 사용해 함수를 만드는 방법의 가장 큰 차이는 **런타임에 받은 문자열을 사용해 함수를 만들 수 있다**는 점이다.

함수 표현식과 함수 선언문은 개발자가 직접 스크립트를 작성해야만 함수를 만들 수 있었다. 그러나 new Function이라는 문법을 사용하면 **어떤 문자열도 함수로 바꿀 수 있다**. 서버에서 전달받은 문자열을 이용해 새로운 함수를 만들고 이를 실행하는 것도 가능하다.

서버에서 코드를 받거나 템플릿을 사용해 함수를 동적으로 컴파일해야 하는 경우, 복잡한 웹 애플리케이션을 구현할 때와 같이 아주 특별한 경우에 new Function을 사용할 수 있습니다.

<br>

### [ 클로저 ]

new Function을 이용해 함수를 만들면 함수의 [[Environment]] 프로퍼티가 현재 렉시컬 환경이 아닌 **전역 렉시컬 환경을 참조**하게 된다. 따라서 new Function을 이용해 만든 함수는 외부 변수에 접근할 수 없고, **오직 전역 변수에만 접근**할 수 있다.

```jsx
// 일반적인 방법
function getFunc() {
  let value = "test";

  let func = function () {
    alert(value);
  };

  return func;
}

getFunc()(); // getFunc의 렉시컬 환경에 있는 값 "test"가 출력된다.
```

```jsx
// new Function
function getFunc() {
  let value = "test";

  let func = new Function("alert(value)");

  return func;
}

getFunc()(); // ReferenceError: value is not defined
```

<br>

### REF

- [MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function)

- [코어 자바스크립트](https://ko.javascript.info/new-function)
