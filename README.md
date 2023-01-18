## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.\
You will also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

# Rule

## Folder Structure

```js
./
├── App.tsx
├── index.tsx
├── apis/
├── assets/
├── components/
│   └── common/
├── hooks/
├── pages/
│   └── Home.tsx
└── types/
```

### Absoulte Path

**import시 절대경로(`@`)를 따른다.**

```json
"baseUrl": ".",
    "paths": {
      "@apis/*": ["src/apis/*"],
      "@assets/*": ["src/assets/*"],
      "@components/*": ["src/components/*"],
      "@common/*": ["src/components/common/*"],
      "@hooks/*": ["src/hooks/*"],
      "@pages/*": ["src/pages/*"],
      "@types/*": ["src/types/*"]
    }

```

### Environment Variable

중요한 key들은 환경변수로 관리한다.

`.env.development.local` 파일과 `.env.production.local` 파일로 분리 후 관리.

환경변수의 선언은 `SNAKE_CASE`를 사용

리액트 파일에서 불러오는 법 : `process.env.REACT_APP_${환경변수}`

## 협업 관련 Rule

### Coding Convention

1. Var문은 사용하지 않는다.

2. 화살표 함수 사용

- 파라미터 하나라도 괄호를 생략하지 않는다.(prettier 규칙: `"arrowParens": "always"`)
- 암시적 반환을 최대한 활용한다.

3. 오브젝트의 프로퍼티에 접근할 때는 Destructuring을 이용한다.

- 새로운 이름으로 변수에 할당 할 때는 꼭 Destructuring을 사용하지 않아도 된다.

```js
// Good
const changeFirstName = user.firstName;

// Good
const { firstName: changeFirstName } = user;
```

4. 변수 등을 조합해서 문자열을 생성하는 경우 템플릿 문자열을 이용한다.

5. 삼중 등호 연산자인 ===, !==만 사용한다.

6. 함수 내에서 반환은 한 번만 한다.

- 단, 예외로 빠져나가는 경우는 제외한다. 코드를 예측하기 쉬우며 흐름이 간결한 함수를 작성할 수 있다.

```js
// Allow
function foo(isValid) {
  ...
  // 예외처리로 바로 빠져나감
  if (!isValid) {
    return;
  }
  ...

  return someDataInTrue;
}
```

7. return문 바로 위는 한 칸 비워 놓는다.

8. 클래스네임은 BEM방식을 따른다.

[js코딩컨벤션 참조url]: https://ui.toast.com/fe-guide/ko_CODING-CONVENTION
[html,css,sass컨벤션 참조url]: https://ui.toast.com/fe-guide/ko_HTMLCSS

### Commit Rule

```
/* 커밋 타입 */
feat : 새로운 기능에 대한 커밋
fix : 버그 수정에 대한 커밋
build : 빌드 관련 파일 수정에 대한 커밋
chore : 그 외 자잘한 수정에 대한 커밋
ci : CI관련 설정 수정에 대한 커밋
docs : 문서 수정에 대한 커밋
style : 코드 스타일 혹은 포맷 등에 관한 커밋
refactor :  코드 리팩토링에 대한 커밋
test : 테스트 코드 수정에 대한 커밋
```

[커밋규칙참조url]: https://beomseok95.tistory.com/328
