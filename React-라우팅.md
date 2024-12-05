### React Router 설치

```bash
npm install --save-dev react-router-dom @types/react-router-dom
```

### 예시

```tsx
import React from 'react';
import { BrowserRouter as Router, Route, Routes, Link } from 'react-router-dom';

// 페이지 컴포넌트
import Home from './pages/Home';
import About from './pages/About';
import Contact from './pages/Contact';

const App = () => {
  return (
    <Router>
      <nav>
        <ul>
          <li>
            <Link to="/">Home</Link>
          </li>
          <li>
            <Link to="/about">About</Link>
          </li>
          <li>
            <Link to="/contact">Contact</Link>
          </li>
        </ul>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/contact" element={<Contact />} />
      </Routes>
    </Router>
  );
};

export default App;
```

### 주요 React Router 개념

- BrowserRouter
  - 브라우저의 History API를 사용해 URL을 관리합니다.
  - 애플리케이션의 최상위 컴포넌트에 감쌉니다.
- Routes
  - 라우팅 구성을 정의하는 컨테이너입니다.
  - <Route> 컴포넌트를 포함하며, 이전 버전의 <Switch>를 대체했습니다.
- Route
  - 특정 경로와 해당 경로에 렌더링할 컴포넌트를 정의합니다.
  - path 속성에 경로를 지정하고, element 속성에 렌더링할 컴포넌트를 설정합니다.
- Link
  - HTML의 <a> 태그와 유사하지만, React Router의 클라이언트 사이드 네비게이션을 제공합니다.
  - 페이지를 새로고침하지 않고 경로를 변경합니다.