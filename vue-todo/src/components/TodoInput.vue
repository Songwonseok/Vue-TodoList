<template>
  <div class="inputBox shadow">
      <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
      <!-- <button v-on:click="addTodo">add</button> -->
      <span class="addContainer" v-on:click="addTodo">
        <i class="fas fa-plus addBtn"></i>
      </span>

      <Modal v-if="showModal" @close="showModal = false">
        <!--
      you can use custom content here to overwrite
      default content
    -->
        <h3 slot="header">경고!
          <!-- v-on:click == @click -->
          <i class="fas fa-times closeModalBtn" @click="showModal = false"></i>
        </h3>
        <div slot="body">
          내용을 입력하세요
        </div>

      </Modal>
  </div>
</template>

<script>
import Modal from './common/Modal.vue'

export default {
  data:function(){
    return{
      newTodoItem:"",
      showModal: false
    }
  },
  methods:{
    addTodo:function(){
      if(this.newTodoItem !== ''){
        this.$emit('addTodoItem',this.newTodoItem);
        this.clearInput();
      } else{
        //alert('Type Something')
        this.showModal = !this.showModal;
      }
    },
    clearInput:function(){
      this.newTodoItem ='';
    }
  },
  components:{
    Modal : Modal
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
    float:right;
  }
</style>