## 🏷 &nbsp;Table of Contents
- [🏷 &nbsp;Table of Contents](#-table-of-contents)
- [🙌 &nbsp;About project](#-about-project)
- [📕 &nbsp;Dev Notes](#-dev-notes)
  - [✔️ &nbsp;HTML과 React의 소스 작성 방식에서의 차이](#️-html과-react의-소스-작성-방식에서의-차이)
  - [✔️ &nbsp;HTML, JavaScript로 counter 구현하기](#️-html-javascript로-counter-구현하기)
  - [✔️ &nbsp;React 컴포넌트 생성하기](#️-react-컴포넌트-생성하기)
  - [✔️ &nbsp;createElement를 JSX로 변환하기](#️-createelement를-jsx로-변환하기)
- [🔫 Troubleshooting](#-troubleshooting)
  - [✔️ &nbsp;html에서 JSX 사용 시 브라우저 렌더링 오류 발생할 때](#️-html에서-jsx-사용-시-브라우저-렌더링-오류-발생할-때)


<br/><br/>

## 🙌 &nbsp;About project

Write Project description.

<br/><br/>

## 📕 &nbsp;Dev Notes

### ✔️ &nbsp;HTML과 React의 소스 작성 방식에서의 차이

HTML은 body에 tag를 작성하여 HTML Element를 생성하는 방식이고, React는 JavaScript 코드로 HTML Element를 만들어서 `ReactDOM` 으로 body에 추가하는 방식이다.

> 잊으면 안 되는 사실이 React는 JavaScript 기반이라는 것이다.

`span` 태그로 글자를 적는 방식에서의 소스를 비교해보면 의미가 와닿는다.


#### HTML
```html
<!DOCTYPE html>
<html>
  <body>
    <span>HI I'm span</span>
  </body>
</html>
```

<br/>

#### React

`createElement` 메서드를 사용하여 `count` 라는 span Element를 생성하고  `ReactDOM.render(count, root);` 를 통해 `root` element에 `count` 를 render하라고 명시해주었다.

```html
<!DOCTYPE html>
<html>
  <body>
    <div id="root"></div>
  </body>
  <script crossorigin src="https://unpkg.com/react@17/umd/react.development.js"></script>
  <script crossorigin src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
  <script>
    const root = document.getElementById('root');
    const coolSpan = React.createElement('span', { id: 'cool-span' }, "HI I'm cool span");
    ReactDOM.render(coolSpan, root);
  </script>
</html>
```

<br/>

### ✔️ &nbsp;HTML, JavaScript로 counter 구현하기 

> 새로운 기술은 불편함을 해소하기 위해 탄생한다.

React는 기존 HTML + JS의 구현 방식의 불편함을 해소하기 위해 탄생했다. HTML과 JS로 counter를 구현하여 어떤 불편함이 있는지 살펴보자.

```html
<!DOCTYPE html>
<html>
  <body>
    <span id="count">Total clicks: 0</span>
    <button id="count-up">Count Up</button>
  </body>
  <script>
    const count = document.querySelector('#count');
    const countUpBtn = document.querySelector('#count-up');

    let counter = 0;
    const handleClick = () => {
      count.innerHTML = `Total clicks: ${++counter}`;
    };

    countUpBtn.addEventListener('click', handleClick);
  </script>
</html>
```

`querySelector` 로 DOM Element에 접근하고, `addEventListener` 메서드를 통해 element에 event를 연결해주는 방식이다.

`countUpBtn` 버튼이 클릭되면 `counter` 를 1 증가시키고 그 값을 `counter.innerHTML` 에 set 해주는 방식이다. React에서는 interactive한 방식으로 이러한 동작을 처리할 수 있다.

<br/>

### ✔️ &nbsp;React 컴포넌트 생성하기

> 아래 예시는 React 동작을 이해하기 위한 것이며, 실제로 사용 시에는 더 간단하게 컴포넌트를 정의할 수 있다.

`React` 의 장점은 HTML에 마크업하지 않고 js로 컴포넌트를 생성할 수 있다는 점이다. 특히 `createElement` 를 통해 컴포넌트를 생성하면서 event handler를 등록할 수 있다.

아래 예시에서는 `onMouseEnter` 와 `onClick` event handler를 등록하고 있다.

```html
<!DOCTYPE html>
<html>
  <body>
    <div id="root"></div>
  </body>
  <script crossorigin src="https://unpkg.com/react@17/umd/react.development.js"></script>
  <script crossorigin src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
  <script>
    const root = document.getElementById('root');
    const span = React.createElement(
      'span',
      {
        key: 'span',
        onMouseEnter: () => console.log('mouse enter')
      },
      "HI I'm span"
    );
    
    const btn = React.createElement(
      'button',
      {
        key: 'btn',
        onClick: () => console.log('im clicked')
      },
      'Click me'
    );

    const container = React.createElement('div', null, [span, btn]);
    ReactDOM.render(container, root);
  </script>
</html>
```

<br/>

### ✔️ &nbsp;createElement를 JSX로 변환하기
실제로 개발할 때는 `createElement` 를 사용하지 않고, JavaScript의 확장된 문법인 JSX를 사용한다. JSX를 사용하여 간단하게 컴포넌트를 정의할 수 있다.

`createElement`

```js
const span = React.createElement(
  'span',
  {
    key: 'span',
    onMouseEnter: () => console.log('mouse enter')
  },
  "HI I'm span"
);
```

<br/>

`JSX`
```js
const Span = (
  <h3 onMouseEnter={() => console.log('mouse enter')}>HI I'm span</h3>
);
```







<br/><br/>

## 🔫 Troubleshooting

### ✔️ &nbsp;html에서 JSX 사용 시 브라우저 렌더링 오류 발생할 때

JSX를 사용하여 html을 작성하고 브라우저로 확인해보면 다음과 같은 오류가 발생한다.

> Uncaught SyntaxError: Unexpected token '<' (at index.html:48:7)

이는 브라우저가 JSX 문법을 이해할 수 없기 때문이다.

JSX를 `createElement` 방식의 JavaScript 코드로 변환해주어야 하며, 이를 위해서는 **Babel**을 설치해주면 된다.

<br/>

CDN을 사용하여 html에 Babel을 import 할 수 있다. Babel을 standalone 방식으로 사용하려면 script 태그에  `type="text/babel">` 을 꼭 넣어주도록 하자.

```diff
<body>
  <div id="root"></div>
</body>
+ <script src="https://unpkg.com/@babel/standalone/babel.min.js"></scritype=>
- <script>
+ <script type="text/babel">
  //...
</script>
```

<br/>

`전체 코드`

JSX를 사용하여 작성한 html도 성공적으로 렌더링이 가능한 것을 확인할 수 있다.

```html
<!DOCTYPE html>
<html>
  <body>
    <div id="root"></div>
  </body>
  <script crossorigin src="https://unpkg.com/react@17/umd/react.development.js"></script>
  <script crossorigin src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
  <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
  <script type="text/babel">
    const root = document.getElementById('root');
    const Span = (
      <h3 key="span" onMouseEnter={() => console.log('mouse enter')}>HI I'm span</h3>
    );

    const Button = (
      <button key="btn" onClick={() => console.log('im clicked')}>Click me</button>
    );
  
    const container = React.createElement('div', null, [Span, Button]);
    ReactDOM.render(container, root);
  </script>
</html>
```