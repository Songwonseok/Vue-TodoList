# Vue.js CRUD 연습을 위한 Todo-List 만들기

## 프로젝트 만들기
```
1. npm install -g @vue/cli
2. vue create '프로젝트 이름' : vue create vue-todo 
- default 선택
3. cd vue-todo
4. 실행 : npm run serve
```

## vue 아이콘 추가
[Font Awesome](https://fontawesome.com/icons?d=gallery)
```
1) 원하는 아이콘 검색
ex) plus 검색

2) Copy HTML 
ex) <i class="fas fa-plus"></i>
```
## Vue단축키
```
1) vue + tab : Vue 기본틀
2) ul>li*3 + tab : ul 태그 + li 태그 3개
```

## 리팩토링
```
App.vue에서 데이터 관리
list의 데이터 + create -> App.vue로 옮김
v-bind : 내려보낼 프롭스 속성 이름
v-on:하위 컴포넌트에서 발생시킨 이벤트 이름="현재 컴포넌트의 메소드명"
UX적인 요소 추가 : Modal
```