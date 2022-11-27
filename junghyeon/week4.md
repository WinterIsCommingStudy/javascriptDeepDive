

arguments는 함수라면 처음부터 갖고 있는 숨겨진 속성인데요. 바로 함수에 들어온 인자를 배열 형식으로 반환합니다. (배열은 아닙니다. 유사 배열이라고 부릅니다.)

```js
function example() {
  console.log(arguments);
}
example(1, 'string', true); // [1, 'string', true]
```
생긴 건 배열이지만, 배열이 아니라 유사 배열이기 때문에, 배열의 메소드는 쓸 수 없습니다.
```js
function example2() {
  console.log(arguments.join()); // Array.prototype.join() 메소드는 사용할 수 없다.
}
example2(1, 'string', true); // Uncaught TypeError: arguments.join is not a function
```
에러가 발생하죠? arguments는 모양만 배열이지 실제 배열이 아니라서 배열의 메소드를 쓰면 에러가 발생합니다.

 

이 때 바로 call이나 apply가 효력을 발휘합니다.

 
```js
function example3() {
  console.log(Array.prototype.join.call(arguments));
}
example3(1, 'string', true); // '1,string,true'
```
배열의 프로토타입에 있는 join 함수를 빌려 쓰는겁니다. this는 arguments를 가리키게 하고요.


1. join() 으로 배열을 문자열로 반환하려고 합니다.

2. 함수 인자로 값들을 넘깁니다. arguments로 배열형태로 받겠지만, 유사배열이라 arguments.join()같은 게 될리가 없죠.

3. 그래서 우선은 프로토타입 메서드 Array.prototype.join()을 불러오고 그 뒤에 .call()로 join함수를 조작합니다.

4. callI(arguments)로 this를 유사배열로 가리키게 합니다. 본래는 Array객체를 가리키고 있지만 바꾼 것이죠. 그러면 Array.prototype.join()이 최종적으로 [1, 'string', true].join() 이 되게 됩니다.

​

join 외에도 slice, concat 등등 모든 메소드를 이 방식으로 사용할 수 있습니다.
