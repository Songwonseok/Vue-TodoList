<template>
  <div class="inputBox shadow">
      <input type="text" v-model="newTodoItem">
      <button v-on:click="addTodo">add</button>
      <span class="addContainer">
        
      </span>
  </div>
</template>

<script>
export default {
  data:function(){
    return{
      newTodoItem:""
    }
  },
  methods:{
    addTodo:function(){
      console.log(this.newTodoItem);
      // 저장하는 로직
      localStorage.setItem(this.newTodoItem, this.newTodoItem);
      this.clearInput();
    },
    clearInput:function(){
      this.newTodoItem ='';
    }
  }
}
</script>

<style scoped>
  input:focus {
    outline: none;
  }
  .inputBox {
    height: 50px;
    border-radius: 5px;
    line-height: 50px;
    background: white;
  }
  .inputBox input {
    border-style: none;
    font-size: 0.9rem;
  }
  .addContainer {
    display: block;
    float: right;
    width: 3rem;
    border-radius: 0 5px 5px 0;
    background: linear-gradient(to right, #6478FB, #8763FB);
  }
  .addBtn {
    color: white;
    vertical-align: middle;
  }
  .closeModalBtn {
    color: #42b983;
  }
</style>