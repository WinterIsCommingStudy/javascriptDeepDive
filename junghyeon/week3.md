## ⛳ TDZ

`const` 변수 선언부터 시작해보자. 변수를 선언하고 초기화하면 변수에 접근할 수 있다. 예상한대로 동작한다.

```jsx
const white = '#FFFFFF';

white; // => '#FFFFFF'
```

이번에는 선언 전에 `white` 변수에 접근해보도록 하겠다.

```jsx
white; // throws `ReferenceError`
const white = '#FFFFFF';

white
```

`**const white = '#FFFFFF'` 구문 전 줄까지, `white` 변수는 TDZ에 있다.**

TDZ에 있는 `white` 변수에 접근하게 되면 , `ReferenceError: Cannot access 'white' before initialization` 자바스크립트 에러가 발생한다.

TDZ에 영향을 받지 않는 구문

`function, var, import`

흥미로운 점으로 `import` 모듈 역시 호이스팅 된다.

`// Works!
myFunction();
import { myFunction } from './myModule';`

`import` 구문이 호이스팅 되기 때문에, 자바스크립트 파일 시작 부분에서 디펜던시 모듈을 가져오는 것이 좋다.

[TDZ을 모른 채 자바스크립트 변수를 사용하지 말라](https://ui.toast.com/weekly-pick/ko_20191014)
