# JavaScript 개요

## JavaScript History
- 자바스크립트는 웹 브라우저에서 동작하는 스크립트 언어이다.
- 초창기의 Front 는 웹 페이지 제작에 보조적인 기능을 수행하였으며 서버로부터 받은 HTML, CSS, 데이터로 렌더링 하는 수준이었다.
- 웹이 발전하면서 서버가 담당하던 역할이 브라우저로 이동하기 시작하면서 자바스크립트가 주목받게 도었다.
- 특히 jQuery 가 등장하면서 DOM 객체를 직접 핸들링하면서 급속히 발전하였다.
- Node.js 의 등장으로 자바스크립트를 이용하여 서버 개발이 가능해졌다.
- React, Vue, Angular, TypeScript 등의 등장으로 자바스크립트를 이용한 개발이 더 용이해졌다.

# JavaScript Data Type

## 구분
- Data Type 은 기본 Type 과 참조 Type 으로 구분한다.

## 기본 Type
- String, Number, Boolean, undefined, null

```
let study1 = 'test';
let study2 = 123;
let study3 = true;
let study4;
let study5 = null;

console.log(study1, typeof study1);
console.log(study2, typeof study2);
console.log(study3, typeof study3);
console.log(study4, typeof study4);
console.log(study5, typeof study5);
```

## 문자 Type
- 작은 따옴표나 큰 따옴표로 생성한다.
- 문자열은 배열처럼 인덱스를 통해서 접근이 가능하다.
- 한번 생성된 문자열은 변경이 불가능하다.

```
let study = 'test';

console.log(study[0]);

study[0] = 'T';

console.log(study, study[0]);

study = 'Test';

console.log(study, study[0]);
```

## 숫자 Type
- 자바는 int, long, float, double 등 다양한 숫자 타입이 존재하지만 자바스크립트는 하나의 숫자형만 존재한다.
- 모든 숫자는 64비트의 부동 소수점 형태로 저장된다.
- 나누기의 경우 소수부분까지 모두 출력됨으로 정수만 필요한 경우는 Math 함수를 활용한다.

## undefined 와 null
- undefined : 값이 할당되지 않은 변수를 의미한다.
- null : 값을 null 로 명시한 변수이다. null 의 typeof는 object 임으로 null 체크시에는 typeof 가 아닌 === null 을 사용하여야 한다.

## 참조 Type
- String, Number, Boolean, null, undefined 와 같은 기본 Type 을 제외한 모든 값윽 객체이다.
- 객체는 Key : Value 구조로 프로퍼티들을 저장하는 컨테이너이다.
- 기본 Type 은 하나의 Value 만 가질 수 있으나 객체는 여러개의 프로퍼티들을 가질 수 있다.
- 객체의 프로퍼티는 기본 타입의 값을 포함하거나 다른 객체를 가리킬 수도 있다.
- 프로퍼티는 함수를 가질 수도 있으며 이때의 프로퍼티를 매서드라고 한다.

## 객체 생성
- 자바는 Class 를 정의하고 Class 의 Instance 를 생성하여 객체를 생성한다.
- 자바스크립트는 Object() 생성자 함수를 활용하거나 객체 리터럴 방식을 이용하여 생성한다.

## Object() 생성자 함수
- 내장 Object() 생성자 함수를 이용하여 빈 객체를 만든 후 프로피터들을 추가한다.

```
let study = new Object();

console.log(study);

study.id = 'testId';
study.val = 'testVal';

console.log(typeof study);
console.log(study);
```

## 객체 리터널
- {} 를 통해서 객체를 생성한다.
- {} 만으로 빈 객체를 생성할 수도 있고 key : value 구조로 프로퍼티를 생성할 수도 있다.
- 프로퍼티값은 자바스크립트가 나타낼 수 있는 모든 값을 SET 할 수 있다.

```
let study = {
  id : 'testId',
  var : 'testVal'
};

console.log(typeof study);
console.log(study);
```

## 객체 프로퍼티 Read / Write / Update / Delete
- [] 표기법, . 표기법 두가지 방법으로 프로퍼티에 접근할 수 있다.
- 프로퍼티에 접근한 후에 값을 Read, Write, Update, Delete 할 수 있다.

```
let study = {
  id : 'testId',
  var : 'testVal'
};

console.log(study['id']);
console.log(study.id);
console.log(study['valNm']);
console.log(study.valNm);

study['id'] = 'testId2';
study.val = 'testVal2';

console.log(study);

study['valNm'] = 'testValNm';
study.remark = 'testRemark';

console.log(study['varNm']);
console.log(study.remark);
console.log(study);

delete study.remark;

console.log(study);
```

- 일반적으로 . 표기법을 많이 사용하나 [] 표기법을 사용해야 할 경우가 있다.

```
let study = {
  id : 'testId',
  val : 'testVal',
  'val-nm' : 'valNm'
};

console.log(study.val-nm);
console.log(study['val-nm']);
```

## for in 문으로 접근
- for in 문을 이용하면 객체에 포함된  모든 프로퍼티에 대해서 루프를 통해 접근이 가능하다.

```
let study = {
  id : 'testId',
  val : 'testVal'
};

for(i in study){
  console.log(study[i]);
}
```

## Type 의 특성 및 유의사항
- 생성된 객체의 변수는 객체 자체에 저장하고 있지 않고 해당 프로퍼티가 가리키는 참조값을 저장한다. 즉 var study = {id : 'testId'} 에서 id 는 testId 라는 값을 저장하는 것이 아니고 testId 라는 문자열 Data 를 가리키는 정보를 저장하고 있다.

```
let study1 = {
  id : 'testId',
  val : 'testVal'
};

let study2 = stury1;

console.log(study1);
console.log(study2);

stury2.id = 'testId2';

console.log(study1);
console.log(study2);
```

- 객체 자체를 비교시에는 참조값이 일치해야 같다고 판단한다.

```
let study1 = {
  id : 'testId',
  val : 'testVal'
};

let study2 = {
  id : 'testId',
  val : 'testVal'
};

let study3 = study2;

console.log(study1 === study2);
console.log(study2 === study3);

console.log(study1.id === study2.id);
console.log(study2.id === study3.id);
```

## 기본 Type 과 Type 의 함수 호출시 Parameter 전달
- 기본 Type 은 값을 복사하여 전달한다.
- 참조 Type 은 값을 복사하지 않고 참조값만 전달한다.

```
let studyBasic = 'test'l
let studyObject = {
  id : 'testId',
  val : 'testVal'
};

function studyFunction(basic, object){
  basic = 'test2';
  object.id = 'testId2';
  
  console.log(basic);
  console.log(studyBasic);
  console.log(object);
  console.log(studyObject);
}

studyFunction(studyBasic, studyObject);

console.log(studyBasic);
console.log(studyObject);
```

## 프로토타입
- 자바스크립트의 모든 객체는 자신의 부모 객체와 연결된다.
- 부모 객체의 프로퍼티는 자신의 객체의 프로퍼티처럼 사용할 수 있다.
- 이러한 부모 객체를 프로토타입이라고 한다.
- toString(), hasOwnProperty() 는 study 에 없는 메서드이지만 에러가 발생하지 ㅇ낳는다.
- study 의 부모인 Object 의 프로퍼티에 이미 정의가 되어 있기 때문이다.
- study 안에 proto 프로퍼티가 부모 객체를 가리키고 있다.

```
let study = {
  id : 'testId',
  var : 'testVal'
};

console.log(study.toString());
console.log(study.hasOwnProperty('id'));

console.log(study);
```

# 배열
- 배열도 객체이다.
- 자바와는 달리 크기를 지정하지 않아도 된다.
- 어떤 타입의 데이터도 저장 가능하며 하나의 배열에 혼횽하여 저장이 가능하다.
- 값을 순차적으로 넣지 않아도 무방하다.

## 배열생성 - Array() 생성자 함수
- new 연산자를 이용한다.
- 일반적으로는 아래의 배열 리터널 방법을 많이 사용한다.

```
let studyArr1 = new Arr(5);
let studyArr2 = new Array(1, '2', true, 4, 5);

console.log(studyArr1);
console.log(studyArr2);
```

## 배열생성 - 배열 리터널
- 대괄호를 이용하여 배열을 생성한다.
- 값이 없는 index 에 접근하였을때 undefined 가 나오는것은 배열도 객체이기 때문이다.

```
let studyArr = ['test', 123, true];

console.log(studyArr[0]);
console.log(studyArr[1]);
console.log(studyArr[2]);
console.log(studyArr[3]);

console.log(typeof studyArr[0]);
console.log(typeof studyArr[1]);
console.log(typeof studyArr[2]);
console.log(typeof studyArr[3]);
```

## 배열의 원소 추가, 수정, 삭제
- 배열의 원소는 Dynamic 하게 추가, 수정, 삭제가 가능하다.
- 추가시 특정 지점을 추가하여 추가가 가능하다. 현재 5번 위치까지 데이터가 있는데 10번 위치에 추가하는 경우 6,7,8,9 는 empty 가 할당된다.
- length 프로퍼티는 데이터의 개수가 아닌 MAX 인덱스 + 1 을 나타내고 만약 0,1,2,100 번째 index 에 요소를 생성하였다면 length 는 100 + 1 인 101 이 된다. 이때 empty 영역은 메모리에 할당되어 있지는 않는다.
- delete 로 배열을 삭제하면 해당 위치가 undefined 가 할당되며 length 값은 변하지 않는다.
- spice() 를 사용하여야 삭제가 가능하다.

```
let studyArr = ['test', 123, true];

studyArr[0] = 'TEST';
studyArr[1] = false;
studyArr[2] = 12345;
studyArr[5] = 'TEST5';

console.log(studyArr[0]);
console.log(studyArr[1]);
console.log(studyArr[2]);
console.log(studyArr[3]);
console.log(studyArr[4]);
console.log(studyArr[5]);

console.log(typeof studyArr[0]);
console.log(typeof studyArr[1]);
console.log(typeof studyArr[2]);
console.log(typeof studyArr[3]);
console.log(typeof studyArr[4]);
console.log(typeof studyArr[5]);

console.log(studyArr.length);

delete studyArr[1];
console.log(sutdyArr);

sutdyArr[100] = 'test100';

console.log(studyArr);

studyArr.length = 10;
console.log(studyArr);
```
```
let studyArr1 = ['test0', 'test1', 'test2'];
let studyArr2 = ['test0', 'test1', 'test2'];
let studyArr3 = ['test0', 'test1', 'test2'];

delete studyArr1[2];
console.log(studyArr1);

studyArr2.splice(1, 2);
console.log(studyArr2);

studyArr3.splice(1, 2, 'Test');
console.log(studyArr3);
```

## Push
- Push 를 통해 배열에 요소를 추가할 수 있다.
- 이때 Max 인덱스 + 1 을 요소에 추가한다.

```
let studyArr = ['test0', 'test1', 'test2'];
studyArr.push('test3');

console.log(studyArr);

studyArr.length = 10;
studyArr.push('test4');

console.log(studyArr);
```

## 배열에 프로퍼티 추가
- 배열도 객체임으로 동적으로 프로퍼티를 추가할 수 있다.
- 배열의 프로퍼티를 추가하는 경우는 length 값은 변하지 않는다.

```
let studyArr = ['test0', 'test1', 'test2'];
studyArr.id = 'studyArrId';
studyArr.val = 'studyArrVal';

console.log(studyArr);
console.log(studyArr.length);
```

## for in 배열
- 배열도 객체임으로 for in 구문을 사용할 수 있다.
- 단, 배열 이외의 프로퍼티도 포함됨으로 for 문을 사용하는 것을 권장한다.

```
let studyArr = ['test0', 'test1', 'test2'];
studyArr.id = 'studyArrId';
studyArr.val = 'studyArrVal';

for(var i in studyArr){
  console.log(studyArr[i]);
}

for(var i=0; i<studyArr.length; i++){
  console.log(studyArr[i]);
}
```

## 배열과 객체 비교
- 배열도 객체이이다. 그러나 약간의 차이가 있다.
- 배열에는 length 프로퍼티가 있고 push 등을 사용할 수 있다.
- 객체의 프로토타입 : Object.prototype
- 배열의 프로토타입 : Array.prototype
- Array.prototype 의 프로토타입 : Object.prototype

```
let studyObj = {
  '0', : 'test0',
  '1', : 'test1',
  '2', : 'test2'
};

let studyArr = ['test0', 'test1', 'test2'];

console.log(typeof studyObj);
console.log(typeof studyArr);

console.log(studyObj.length);
console.log(studyArr.length);

console.log(studyObj);
console.log(studyArr);

console.log(studyObj.__proto__);
console.log(studyArr.__proto__);
```

# 연산자
## + 연산자
- 문자열인 경우는 문자열을 연결한다.
- 숫자인 경우는 더하기 연산을 한다.

```
let study1 = 1 + 1;
let study2 = 'test' + 'test';
let study3 = 1 + 'test';

console.log(study1);
console.log(study2);
console.log(study3);
```

## typeof 연산자
- 데이터의 타입을 리턴한다.

```
let study1 = 'a';
let study2 = 1;
let study3 = true;
let study4 = null;
let study5;
let study6 = {};
let study7 = [];
let study8 = function (){};

console.log(typeof study1);
console.log(typeof study2);
console.log(typeof study3);
console.log(typeof study4);
console.log(typeof study5);
console.log(typeof study6);
console.log(typeof study7);
console.log(typeof study8);
```

## ==, === 연산자
- == 왼쪽과 오른쪽의 타입이 다른 경우 형변환후에 비교한다.
- === 왼쪽과 오른쪽의 타입, Value 를 동시에 비교한다.

```
let study1 = '1';
let study2 = 1;

console.log(study1 == study2);
console.log(study1 === study2);
```

## !!연산자
- Value 값을 Boolean 값으로 변환한다.

```
let study1 = 'a';
let study2 = 1;
let study3 = true;
let study4 = null;
let study5;
let study6 = {};
let study7 = [];
let study8 = function (){};

console.log(!!study1);
console.log(!!study2);
console.log(!!study3);
console.log(!!study4);
console.log(!!study5);
console.log(!!study6);
console.log(!!study7);
console.log(!!study8);
```

# 함수
## 개요
- 함수도 객체이다.
- 함수에 함수명은 선택사항이다.
- 함수명이 없는 함수는 익명함수라고 한다.
- 함수를 변수에 할당하거나, 인자로 전달, return 값으로 활용할 수 있다.

```
let study1 = function(x, y){
  return x + y;
};

let study2 = study1;

console.log(study1(1, 2));
console.log(study2(3, 4));
```

- 위에서 study1 은 변수이고 함수는 이름이 없음으로 익명함수이다.
- study1 은 익명함수를 참조하는 것이고 익명함수는 참조 Type 인 객체임으로 study1 과 study2 는 같은 익명함수를 참조한다.
- 익명함수는 변수에 () 를 붙여서 호출한다.
- 변수에 할당한 함수의 함수이름으로는 외부에서 접근이 불가하다.

```
let study1 = function study2(x, y){
  return x + y;
};

console.log(study1(1, 2));
console.log(study2(1, 2));
```

- 일반적으로 변수에 할당하는 함수에는 함수명을 사용하지 않으나 함수 안에서 함수를 재귀로 호출할 경우는 사용한다.

```
let study1 = function study2(x, y){
  console.log('STUDY', x + y);
  
  if(x + y < 10){
    return true;
  }
  
  return study2(x, x + y);
};

console.log(study1(1, 2));
```

## 함수 호이스팅
- 함수는 코드 위치와 상관없이 먼저 생성된다.

```
console.log(study1);
console.log(study2(1, 2));
console.log(study3(1, 2));

let study1 = 'test';

function study2(x, y){
  return x + y;
}

let study3 = function(x, y){
  return x + y;
}
```

## 함수 프로퍼티
- 함수도 객체임으로 프로퍼티를 가질 수 있다.

```
function study1(x, y){
  return x + y;
}

study1.testVal1 = function(x, y){
  return x * y;
};

study1.testVal2 = study1(1, 2);

study1.testVal3 = 'test';

console.log(study1.testVal1(2, 3));
console.log(study1.testVal2);
console.log(study1.testVal3);
```

## 함수 할당
- 함수도 객체임으로 변수나 배열, 프로퍼티값등으로 할당할 수 있다.

```
let study1 = function(x, y){
  return x + y;
};

let study2 = [];
study2[0] = test;

let study3 = {};

study3.testVal = test;

console.log(study1(1, 2));
console.log(study2[0](2, 3));
console.log(study3.testVal(3, 4));

study1.id = 'testId';

console.log(study1.id);
console.log(study2[0].id);
console.log(study3.testVal(3, 4));

sutdy1.id = 'testId';

console.log(study1.id);
console.log(study2[0].id);
console.log(study3.testVal.id);

sutdy3.testVal.val = 'testVal';

console.log(study1.val);
console.log(study2[0].val);
console.log(study3.testVal.val);
```

## 함수를 인자로 전달
- 함수도 객체임으로 함수 실행시 인자로 전단할 수 있다.

```
let study1 = function(func){
  console.log(typeof func);
  console.log(func(1, 2));
};

let study2 = function(x, y){
  return x + y;
};

console.log(study1(study2));
```

## 함수를 return 값으로 활용
- 함수를 return 값으로 사용할 수 있다.

```
let study1 = function(x, y){
  return function(){
    return x + y;
  }
};

let study2 = study1(1, 2);
let study3 = study3(2, 3);

console.log(study2());
console.log(study3());

study1.id = 'testId';

console.log(study1.id);
console.log(study2.id);
console.log(study3.id);
```

## 함수의 내부 프로퍼티
- 배열에 length 와 같은 내부 프로퍼티가 있던것처럼 함수에도 내부 프로퍼티가 존재한다.

```
let study1 = function(x, y){

};

console.dir(study1);
```

- name 은 함수의 이름이다.
- caller 는 자신을 호출한 함수이다.
- length 는 함수에 정의한 인자의 개수이다.
- arguments 는 인자로 받아온 값을 저장하는 객체 함수에 정의된 인자보다 적게 호출하였을 경우 넘겨지지 않은 인자는 undefined 값이 할당된다.
- 함수에 정의된 인자보다 많게 호출하였을 경우는 초과된 인수는 무시한다.
- length 프로퍼티는 전달된 인자의 개수에 따른 처리를 해주어야 하는 함수를 개발할 때 사용한다. 배열의 length 와는 다르다.

```
let study1 = function(x, y){
  console.dir(arguments);
};

console.dir(study1(1));
console.dir(study1(1, 2));
console.dir(study1(1, 2, 3));
console.dir(study1(1, 2, 3, 4));
```

- prototype 은 앞서 설명한 prototype 이나 proto 와는 다른 개념이다.
- 이 함수를 이용하여 만든 객체의 prototype 이 함수의 prototype 이 된다.

## 콜백함수
- 어떠한 이벤트가 발생하거나 특정 시점에 도달하였을때 호출되는 함수이다.
- xxxEvent 가 호출되면 함수가 즉시 수행된다.

## 즉시 실행 함수
- 함수를 정의하면서 바로 실행되는 함수를 즉시 실행 함수라고 한다.
- 함수를 () 로 감싸서 만든 후에 바로 호출한다.
- 익명 함수로 만들면 최초 한번 실행 후 다시 호출할 수 없기 때문에 초기 실행하는 코드에 사용한다.
- 자바스크립트 프레임워크나 라이브러리 소스들에서 사용한다.

```
(function(x, y){
  console.log(x + y);
}(1, 2);
```

## 즉시 실행 함수를 사용하는 이유
- 함수 내부에서 사용한 변수는 함수 내부에서만 유효하다.
- 즉시 실행 함수를 사용하여 내부에 만든 변수는 함수 외부에서 접근이 불가하다.
- 전역 공간을 사용하지 않기 때문에 다른 소스나 라이브러리와의 네이밍 충돌을 예방할 수 있다.

```
function sutdy1(){
  let a = 'testA';
  let b = 'testB';

  function chgB(){
    b = 'chgTestB';
  }
  
  console.log(a);
  console.log(b);
  
  chgB();
  
  console.log(b);
 }
 
 study1();
 console.log(a);
 chgB();
 ```
 
 ## 클로저
 - 함수 내부에 생성한 내부 함수는 함수내에서만 사용 가능하며 외부에서는 접근이 불가하다.
 - 그러나 내부 함수를 함수의 return 으로 사용하는 경우에는 외부에서 접근이 가능하게 된다.

```
function study1(){
  let a = 'testA';
  let b = 'testB';
  
  function chgB(){
    b = 'chgTestB';
    console.log(b);
  }
  
  return chgB();
}

study1();
```

## 함수 리턴
- 함수도 객체임으로 함수를 return 할 수 있다.
- 위의 클로저를 통해 이미 확인하였다.
- 리턴한 함수를 객체에 할당할 수도 있다.

```
function study1(x, y){
  console.log(x + y);
  
  return function(x, y){
    console.log(x * y);
  }
}

let work = study1(2, 3);
work(2, 3);
console.log(work);
```

## 리턴
- 함수는 항상 return 값을 반환한다.
- return 을 명시하지 않아도 return 을 한다.

### return 을 하지 않는 경우
```
let study1 = function(id, val){
  this.id = id;
  this.val = val;
};

let study2 = {
  studyFunction : function(id, val){
    this.id = id;
    this.val = val;
  }
};

let result1 = study1();
let result2 = study2.testFunction();
let result3 = new Study1('ID', 'VAL');
let result4 = new Study2.testFunction('ID2', 'VAL2');

console.log(result1);
console.log(result2);
console.log(result3);
console.log(result4);
```
