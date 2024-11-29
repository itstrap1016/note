### React로 사고하기

- props, state가 변경되면 렌더링 사이클이 생긴다.
- 자식 컴포넌트에서 setState 함수를 호출 -> 부모 컴포넌트에서 setState 함수 실행 -> state 변경 -> state 자식 컴포넌트에게 다시 전달
