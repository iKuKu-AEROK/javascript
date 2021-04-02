# JavaScript 개요
<br/>
## JavaScript History
- 자바스크립트는 웹 브라우저에서 동작하는 스크립트 언어이다.
- 초창기의 Front 는 웹 페이지 제작에 보조적인 기능을 수행하였으며 서버로부터 받은 HTML, CSS, 데이터로 렌더링 하는 수준이었다.
- 웹이 발전하면서 서버가 담당하던 역할이 브라우저로 이동하기 시작하면서 자바스크립트가 주목받게 도었다.
- 특히 jQuery 가 등장하면서 DOM 객체를 직접 핸들링하면서 급속히 발전하였다.
- Node.js 의 등장으로 자바스크립트를 이용하여 서버 개발이 가능해졌다.
- React, Vue, Angular, TypeScript 등의 등장으로 자바스크립트를 이용한 개발이 더 용이해졌다.
<br/>
# JavaScript Data Type
<br/>
## 구분
- Data Type 은 기본 Type 과 참조 Type 으로 구분한다.
<br/>
## 기본 Type
- String, Number, Boolean, undefined, null

```
var study1 = 'test';
var study2 = 123;
var study3 = true;
var study4;
var study5 = null;

console.log(study1, typeof study1);
console.log(study2, typeof study2);
console.log(study3, typeof study3);
console.log(study4, typeof study4);
console.log(study5, typeof study5);
```
<br/>
## 문자 Type
- 작은 따옴표나 큰 따옴표로 생성한다.
- 문자열은 배열처럼 인덱스를 통해서 접근이 가능하다.
- 한번 생성된 문자열은 변경이 불가능하다.

```
var study = 'test';

console.log(study[0]);

study[0] = 'T';

console.log(study, study[0]);

study = 'Test';

console.log(study, study[0]);
```
<br/>
## 숫자 Type
- 자바는 int, long, float, double 등 다양한 숫자 타입이 존재하지만 자바스크립트는 하나의 숫자형만 존재한다.
- 모든 숫자는 64비트의 부동 소수점 형태로 저장된다.
- 나누기의 경우 소수부분까지 모두 출력됨으로 정수만 필요한 경우는 Math 함수를 활용한다.
<br/>
## undefined 와 null
- undefined : 값이 할당되지 않은 변수를 의미한다.
- null : 값을 null 로 명시한 변수이다. null 의 typeof는 object 임으로 null 체크시에는 typeof 가 아닌 === null 을 사용하여야 한다.
<br/>
## 참조 Type
- String, Number, Boolean, null, undefined 와 같은 기본 Type 을 제외한 모든 값윽 객체이다.
- 객체는 Key : Value 구조로 프로퍼티들을 저장하는 컨테이너이다.
- 기본 Type 은 하나의 Value 만 가질 수 있으나 객체는 여러개의 프로퍼티들을 가질 수 있다.
- 객체의 프로퍼티는 기본 타입의 값을 포함하거나 다른 객체를 가리킬 수도 있다.
- 프로퍼티는 함수를 가질 수도 있으며 이때의 프로퍼티를 매서드라고 한다.
<br/>
## 객체 생성
- 자바는 Class 를 정의하고 Class 의 Instance 를 생성하여 객체를 생성한다.
- 자바스크립트는 Object() 생성자 함수를 활용하거나 객체 리터럴 방식을 이용하여 생성한다.
<br/>
## Object() 생성자 함수
- 내장 Object() 생성자 함수를 이용하여 빈 객체를 만든 후 프로피터들을 추가한다.

```
var study = new Object();

console.log(study);

study.id = 'testId';
study.val = 'testVal';

console.log(typeof study);
console.log(study);
```
<br/>
## 객체 리터널
- {} 를 통해서 객체를 생성한다.
- {} 만으로 빈 객체를 생성할 수도 있고 key : value 구조로 프로퍼티를 생성할 수도 있다.
- 프로퍼티값은 자바스크립트가 나타낼 수 있는 모든 값을 SET 할 수 있다.

```
var study = {
  id : 'testId',
  var : 'testVal'
};

console.log(typeof study);
console.log(study);
```
<br/>
## 객체 프로퍼티 Read / Write / Update / Delete
- [] 표기법, . 표기법 두가지 방법으로 프로퍼티에 접근할 수 있다.
- 프로퍼티에 접근한 후에 값을 Read, Write, Update, Delete 할 수 있다.

```
var study = {
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
var study = {
  id : 'testId',
  val : 'testVal',
  'val-nm' : 'valNm'
};

console.log(study.val-nm);
console.log(study['val-nm']);
```
<br/>
## for in 문으로 접근
- for in 문을 이용하면 객체에 포함된  모든 프로퍼티에 대해서 루프를 통해 접근이 가능하다.

```
var study = {
  id : 'testId',
  val : 'testVal'
};

for(i in study){
  console.log(study[i]);
}
```
<br/>
## Type 의 특성 및 유의사항
- 생성된 객체의 변수는 객체 자체에 저장하고 있지 않고 해당 프로퍼티가 가리키는 참조값을 저장한다. 즉 var study = {id : 'testId'} 에서 id 는 testId 라는 값을 저장하는 것이 아니고 testId 라는 문자열 Data 를 가리키는 정보를 저장하고 있다.

```
var study1 = {
  id : 'testId',
  val : 'testVal'
};

var study2 = stury1;

console.log(study1);
console.log(study2);

stury2.id = 'testId2';

console.log(study1);
console.log(study2);
```

- 객체 자체를 비교시에는 참조값이 일치해야 같다고 판단한다.

```
var study1 = {
  id : 'testId',
  val : 'testVal'
};

var study2 = {
  id : 'testId',
  val : 'testVal'
};

var study3 = study2;

console.log(study1 === study2);
console.log(study2 === study3);

console.log(study1.id === study2.id);
console.log(study2.id === study3.id);
```
<br/>
## 기본 Type 과 Type 의 함수 호출시 Parameter 전달
- 기본 Type 은 값을 복사하여 전달한다.
- 참조 Type 은 값을 복사하지 않고 참조값만 전달한다.

```
var studyBasic = 'test'l
var studyObject = {
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
<br/>
## 프로토타입
- 자바스크립트의 모든 객체는 자신의 부모 객체와 연결된다.
- 부모 객체의 프로퍼티는 자신의 객체의 프로퍼티처럼 사용할 수 있다.
- 이러한 부모 객체를 프로토타입이라고 한다.
- toString(), hasOwnProperty() 는 study 에 없는 메서드이지만 에러가 발생하지 ㅇ낳는다.
- study 의 부모인 Object 의 프로퍼티에 이미 정의가 되어 있기 때문이다.
- study 안에 proto 프로퍼티가 부모 객체를 가리키고 있다.

```
var study = {
  id : 'testId',
  var : 'testVal'
};

console.log(study.toString());
console.log(study.hasOwnProperty('id'));

console.log(study);
```
