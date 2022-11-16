## 변수

- 변수란 메모리 주소(Memory address)에 접근하기 위해 사람이 이해할 수 있는 언어로 지정한 식별자(identifier)이다.

<aside>
📌 식별자란 변수명, 함수명, 프로퍼티명, 클래스명 등이 있다.

</aside>

변수이름을 비롯한 모든 식별자는 실행컨텍스트에 등록된다

실행컨텍스트는 실행하기위한 환경을 제공하고 관리한다.

호이스팅

- 선언된 변수를 어디서나 사용 할 수있음

변수네이밍

- 예약어 불가
- 첫 글자 숫자 불가

**var를 쓰지 않는 이유**

- 함수 레벨 스코프
- var 키워드 생략 허용
- 중복 선언 허용
- 변수 호이스팅

## 표현식과 문

표현식은 값으로 평가될 수 있는 문

문은 var, function과 같은 선언 키워드를 사용하여 변수나 함수를 생성하기도 하고 if, for, while 문과 같은 제어문을 생성하여 프로그램의 흐름을 제어하기도 한다. 표현식을 통해 평가한 값을 통해 실제로 컴퓨터에게 명령을 하여 무언가를 하는 것은 문이다

## 데이터 타입

### 원시 타입 (primitive data type)

- `boolean`
- `null`
- `undefined`
- `number`
- `string`
- `symbol` (ES6에서 추가)

변경 불가능한 값 

**number**

```jsx
var integer = 10;        // 정수
var double = 10.12;      // 실수
var negative = -20;      // 음의 정수
var binary = 0b01000001; // 2진수
var octal = 0o101;       // 8진수
var hex = 0x41;          // 16진수

```

2진수, 8진수, 16진수 리터럴은 메모리에 동일한 배정밀도 64비트 부동소수점 형식의 2진수로 저장된다. 자바스크립트는 2진수, 8진수, 16진수 데이터 타입을 제공하지 않기 때문에 이들 값을 참조하면 모두 10진수로 해석된다.

```jsx
console.log(binary); // 65
console.log(octal);  // 65
console.log(hex);    // 65

// 표기법만 다를뿐 같은 값이다.
console.log(binary === octal); // true
console.log(octal === hex);    // true
```

**undefined**

undefined는 개발자가 의도적으로 할당한 값이 아니라 자바스크립트 엔진에 의해 초기화된 값이다. 변수를 참조했을 때 undefined가 반환된다면 참조한 변수가 선언 이후 값이 할당된 적인 없는 변수

**null**

프로그래밍 언어에서 `null`
은 의도적으로 변수에 값이 없다는 것을 명시할 때 사용

자바스크립트 엔진은 누구도 참조하지 않는 메모리 영역에 대해 [가비지 콜렉션](https://developer.mozilla.org/ko/docs/Web/JavaScript/Memory_Management)
을 수행

### 객체 타입 (object/reference type)

- `object`

