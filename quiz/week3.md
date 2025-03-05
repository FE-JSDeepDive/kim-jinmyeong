Q1) 아래 console의 값과 그 이유는?
```
let foo = 1 // 전역변수
{
	console.log(foo); -> ?
	let foo = 2; // 지역 변수
}
```

A1) ReferenceError: Cannot access 'foo' before initialization 에러발생

let이 변수 호이스팅이 일어나지 않는다면 console.log(foo)는 스코프 체이닝을 타고가서 전역변수 foo의 값을 참조했어야 한다. 
그러나 블록 스코프 안에서 지역변수 let foo 의 호이스팅이 일어났기 때문에 전역변수가 아닌 지역변수 let foo에 접근하게 되어 참조에러를 발생시킨것


Q2) 아래 console의 값과 그 이유는?
```
var foo = 1 // 전역변수
{
	console.log(foo); -> ?
	var foo = 2; // 지역 변수
}
```
A2) `1` 출력
var로 선언한 경우 var는 함수 레벨 스코프이기 때문에 전역 변수인 var foo 와 동일한 스코프를 가진다.
따라서 전역변수 foo와 전역변수 foo는 아래와 같이 호이스팅된다
```jsx
var foo;// 중복 선언된 변수는 무시된다
var foo; // 호이스팅된 선언 (값은 undefined)

foo = 1;  // 초기화는 원래 위치에서 발생
{
    console.log(foo);  // 1
    foo = 2;  // 재할당 (새로운 변수가 아님)
}
```
전역 스코프에서 `foo` 변수는 중복선언 되어 하나는 무시된다. 이후 foo 에는 1이 할당되고 다음 줄에서 console은 1이 할당되어있는 foo를 참조한다.