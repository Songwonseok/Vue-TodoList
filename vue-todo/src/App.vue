<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:addTodoItem="addOneItem" ></TodoInput> <!-- v-on:하위 컴포넌트에서 발생시킨 이벤트 이름="현재 컴포넌트의 메서드 명" -->
    <TodoList v-bind:propsdata="todoItems" 
    v-on:removeTodoItem="removeOneItem"
    v-on:toggleCompleteTodo="toggleItem"></TodoList> <!-- v-bind:내려보낼 프롭스 속성 이름="현재 위치의 컴포넌트 데이터 속성" -->
    <TodoFooter v-on:clearTodoItems="clearAll"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoFooter from './components/TodoFooter.vue'
import TodoList from './components/TodoList.vue'
import TodoInput from './components/TodoInput.vue'

export default {
  data(){
    return {
      todoItems : []
    }
  },
  // 인스턴스 생성되는 시점에서 실행됨
 
  methods:{
    addOneItem(todoItem){
      const obj = {completed:false, item : todoItem};
      localStorage.setItem(todoItem, JSON.stringify(obj));
      this.todoItems.push(obj);
    },
    removeOneItem(todoItem,index){
      localStorage.removeItem(todoItem.item);
      this.todoItems.splice(index, 1); // index에서 1개를 지움
    },
    clearAll(){
      localStorage.clear();
      //this.todoItems.splice(0);
      this.todoItems = [];
    },
    toggleItem(todoItem, index){
      this.todoItems[index].completed = !this.todoItems[index].completed
      //로컬 스토리지에 데이터를 갱신
      localStorage.removeItem(todoItem.item);
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
    }
  },
  components: {
    TodoHeader,
    TodoFooter,
    TodoList,
    TodoInput
  }
}
</script>

<style>
body{
    text-align: center;
    background-color: #f6f6f6;
}
input {
  border-style: groove;
  width:200px;
}
button {
  border-style: groove;
}
.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}

</style>
