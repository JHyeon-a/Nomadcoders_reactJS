# Creat React

## 1. 설치

[리액트 공식문서 바로가기](https://ko.legacy.reactjs.org/docs/create-a-new-react-app.html)

(node.js 있다고 가정)

#### 1. 터미널에 다음과 같은 명령어 실행

```
npx create-react-app my-app
cd my-app
npm start
```

- 여기서 my-app은 프로젝트명

#### 2. 필요 없는 기본 파일들 지우기

- `src` 디렉토리 안의 `App.js` 파일과 `index.js` 파일만 남겨두고 삭제
- `App.js`는

  ```js
  function App() {
    return (
      <div>
        <h1>Welcom back!!</h1>
      </div>
    );
  }

  export default App;
  ```

  요 형태로 두기

- 마찬가지로 `index.js`도

  ```js
  import React from "react";
  import ReactDOM from "react-dom/client";
  import App from "./App";

  const root = ReactDOM.createRoot(document.getElementById("root"));
  root.render(
    <React.StrictMode>
      <App />
    </React.StrictMode>
  );
  ```

  요정도만 남겨두기

#### 3. (선택) prop-types 설치

```
npm i prop-types
```

원하는 컴포넌트 안에 prop-types import 하기

```js
import PropTypes from "prop-types";
```

## 2. 컴포넌트 생성

`Button.js` 컴포넌트 생성 후 내보내기 (App.js에서 보여주기 위해)

```js
export default Button;
```

`App.js`에서 `Button.js` 컴포넌트 사용을 위해 입력

```js
import Button from "./Button";
```

컴포넌트 뿐만 아니라 styles.css와 같은 파일도

```js
import "./styles.css";
```

이렇게 임포트하면 사용 가능함

### ✅ css 파일은 다음과 같은 `분할 정복` 방식을 추천함

`Button.module.css` 파일

```css
.btn {
  color: white;
  background-color: tomato;
}
```

`Button.js` 파일

```js
import PropTypes from "prop-types";
//이렇게 css 파일을 임포트하고
import styles from "./Button.module.css";

function Button({ text }) {
  //이렇게 clasName을 {styles.(클래스명)} 적기
  return <button className={styles.btn}>{text}</button>;
}

Button.propTypes = {
  text: PropTypes.string.isRequired,
};

export default Button;
```

이렇게 하면 같은 css를 적용해야 하는 컴포넌트에 같은 방식으로 해당 클래스만 css를 입혀줄 수 있음!
