### Node.js 초기화

- npm init -y

### React 및 React DOM 설치

```bash
npm install react react-dom
```

### TypeScript 및 타입 정의 설치

```bash
npm install --save-dev typescript @types/react @types/react-dom
```

### Webpack 및 관련 플러그인 설치

```bash
npm install --save-dev webpack webpack-cli webpack-dev-server ts-loader html-webpack-plugin clean-webpack-plugin
```

- React 애플리케이션 빌드에 필요한 webpack과 관련 플러그인을 설치합니다.
- webpack: 모듈 번들러.
- webpack-cli: Webpack 명령줄 도구.
- webpack-dev-server: 개발용 서버.
- ts-loader: TypeScript 파일을 Webpack에서 로드.
- html-webpack-plugin: HTML 파일을 생성 및 관리.
- clean-webpack-plugin: 빌드 디렉토리를 정리.

### 프로젝트 구조 설정

- my-react-app/
  ├── public/
  │ └── index.html
  ├── src/
  │ ├── index.tsx
  │ └── App.tsx
  ├── tsconfig.json
  ├── webpack.config.js
  └── package.json

### TypeScript 설정 (tsconfig.json)

```json
{
  "compilerOptions": {
    "target": "ES6",
    "module": "ES6",
    "jsx": "react-jsx",
    "moduleResolution": "node",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true
  },
  "include": ["src"]
}
```

### Webpack 설정 (webpack.config.js)

```javascript
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const { CleanWebpackPlugin } = require('clean-webpack-plugin');

module.exports = {
  entry: './src/index.tsx',
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist'),
  },
  resolve: {
    extensions: ['.ts', '.tsx', '.js'],
  },
  module: {
    rules: [
      {
        test: /\.tsx?$/,
        use: 'ts-loader',
        exclude: /node_modules/,
      },
    ],
  },
  plugins: [
    new CleanWebpackPlugin(),
    new HtmlWebpackPlugin({
      template: './public/index.html',
    }),
  ],
  devServer: {
    static: './dist',
    port: 3000,
    open: true,
  },
};
```

### HTML 템플릿 생성 (public/index.html)

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>React + TypeScript</title>
  </head>
  <body>
    <div id="root"></div>
  </body>
</html>
```

### React 엔트리 포인트 (src/index.tsx)

```tsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';

ReactDOM.createRoot(document.getElementById('root')!).render(<App />);
```

### React 컴포넌트 (src/App.tsx)

```tsx
import React from 'react';

const App: React.FC = () => {
  return <h1>Hello, React + TypeScript!</h1>;
};

export default App;
```

### 스크립트 추가 (package.json)

- package.json에 Webpack 실행 스크립트를 추가합니다.

```json
"scripts": {
  "start": "webpack serve --mode development",
  "build": "webpack --mode production"
}
```

### 개발 서버 실행

```bash
npm start
```

### 프로덕션 빌드

```bash
npm run build
```
