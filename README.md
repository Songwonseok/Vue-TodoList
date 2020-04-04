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
## Vue Tip
```
1) vue + tab : Vue 기본틀
2) ul>li*3 + tab : ul 태그 + li 태그 3개
```

## 리팩토링 + 복습
```
- App.vue에서 데이터 관리
- list의 데이터 + create -> App.vue로 옮김
- v-bind : 내려보낼 프롭스 속성 이름
- v-on:하위 컴포넌트에서 발생시킨 이벤트 이름="현재 컴포넌트의 메소드명"
- v-bind:class="{checkBtnCompleted : todoItem.completed}" : todoItem.completed가 true면 checkBtnCompleted 클래스 사용
- UX적인 요소 추가 : Modal, Transition
```

## Modal
[Vue 공식홈페이지](https://vuejs.org/v2/examples/modal.html)

```
사용법
1. learn - examples - Modal Component
2. common 폴더 생성 - Modal.vue 생성
3. example html에서 <transition name="modal">내용을 Modal.vue <template>에 복사
4. example css를 Modal.vue <style>에 복사
5.. 상위 컴포넌트에 showModal: false data 추가
6. slot 수정

slot이란?
- 특정 컴포넌트의 일부 UI를 재사용할 수 있는 기능
```

## Transition
[Vue 공식홈페이지](https://vuejs.org/v2/guide/transitions.html#List-Transitions)
```
- 트랜지션을 입힐 때는 클래스의 이름에 따라서 달라짐
- v-enter-active / v-leave-active 2가지
- v-enter(이펙트 시작) -> v-enter-to / v-leave -> v-leave-to(없어짐)
- Opacity는 보통 v-enter == v-leave-to  / v-enter-to == v-leave
- Opactity : 0 (안보임) / 1(생김)

사용법
1. example css를 <style>에 복사
2. <transition-group name="list" tag="p">를 <template>안으로 복사 이때 tag는 사용할 태그로 수정
```

vue 장점
- 애니메이션이나 트랜지션이 프레임워크 자체적으로 제공되서 디자이너와 퍼블리셔들이 좋아하는 기능이 많음
- 가벼움
- 진입장벽이 낮음
- 