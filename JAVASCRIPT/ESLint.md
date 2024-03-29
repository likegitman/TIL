# ESLint
> ES + Lint, ES는 Ecma(European Computer Manufacturers Association) Script, 자바스크립트를 뜻하고 Lint는 보푸라기라는 뜻이다. 프로그래밍에서Lint는  
> 에러가 있는 코드에 표시를 달아놓는 것을 의미한다. 따라서 ESLint는 자바스크립트 문법 중 에러가 있는 곳에  
> 표시를 다는 도구이다.

## 장점
### 1. 사용자가 직접 정의한대로 코드를 점검하고 에러를 표시해준다.
### 2. 문법 에러뿐만 아니라 코딩 스타일도 정할 수 있어서 협업에 도움이된다.
> 개발자마다 코딩 스타일의 차이가 있는데 팀에서 코딩스타일을 하나로 정하고 ESLint에 설정을하면  
> 코드를 같은 사람이 코딩한것 같이 보여서 통일성에 큰 도움이 될 수 있다.

## Example
```js
{
  "root": true,
  "env": {
    "es2015": true,
    "node": true,
    "browser": true
  },
  "extends": [
    "next/core-web-vitals",
    "eslint:recommended",
    "plugin:@typescript-eslint/recommended",
    "prettier"
  ],
  "parser": "@typescript-eslint/parser",
  "parserOptions": {
    "ecmaVersion": 12,
    "sourceType": "module"
  },
  "plugins": ["@typescript-eslint"],
  "ignorePatterns": ["node_modules/**", "**/dist/**"],
  "rules": {
    "react-hooks/exhaustive-deps": "off",
    "@typescript-eslint/no-unused-vars": [
      "error",
      {
        "argsIgnorePattern": "^_",
        "varsIgnorePattern": "^_"
      }
    ],
    "@typescript-eslint/no-var-requires": "off"
  }
}
```
