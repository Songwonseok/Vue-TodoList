<template>
  <div class="clearAllContainer">
      <sapn class="clearAllBtn" v-on:click="clearTodo">Clear All</sapn>
  </div>
</template>

<script>
export default {
  methods:{
    clearTodo:function(){
      this.$emit('clearTodoItems');
    }
  }
}
</script>
<style scoped>
.clearAllContainer {
  width: 8.5rem;
  height: 50px;
  margin: 0 auto;
  line-height: 50px;
  border-radius: 5px;
  background-color: white;
} 
.clearAllBtn {
  display: block;
  color: #e20303;
}
</style>