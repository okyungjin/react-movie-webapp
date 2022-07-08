## 🏷 &nbsp;Table of Contents
- [🏷 &nbsp;Table of Contents](#-table-of-contents)
- [🙌 &nbsp;About project](#-about-project)
- [📕 &nbsp;Dev Notes](#-dev-notes)
  - [✔️ &nbsp;HTML과 React의 소스 작성 방식에서의 차이](#️-html과-react의-소스-작성-방식에서의-차이)
  - [✔️ &nbsp;Why is React awesome?](#️-why-is-react-awesome)
- [🔫 Troubleshooting](#-troubleshooting)
  - [✔️ &nbsp;TIL 3](#️-til-3)


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



<br/><br/>

## 🔫 Troubleshooting

### ✔️ &nbsp;TIL 3
