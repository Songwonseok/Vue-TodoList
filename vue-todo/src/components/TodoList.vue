<template>
  <div>
      <ul>
        <li v-for="(todoItem, index) in todoItems" v-bind:key="todoItem.item" class="shadow">
          <i class="fas fa-check checkBtn" v-bind:class="{checkBtnCompleted:todoItem.completed}"
          v-on:click="toggleComplete(todoItem)"></i>
          <span v-bind:class="{textCompleted: todoItem.completed}"> <!-- todoItem.completed가 true면 저 클래스 사용 -->
            {{ todoItem.item }}
            </span>
          <span v-on:click="removeTodo(todoItem,index)" class="removeBtn">
            <i class="fas fa-trash-alt"></i>
          </span>
        </li>
      </ul>
  </div>
</template>

<script>
export default {
  data : function(){
    return{
      todoItems: []
    }
  },
  // 인스턴스 생성되는 시점에서 실행됨
  created:function(){
    if(localStorage.length > 0){
      for (var i=0; i<localStorage.length;i++){
        if(localStorage.key(i) !== 'loglevel:webpack-dev-server')
          this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
          //this.todoItems.push(localStorage.key(i)
        //console.log(localStorage.key(i))
      }
    }
  },
  methods:{
    removeTodo:function(todoItem,index){
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1); // index에서 1개를 지움
      //this.todoItems.
    },
    toggleComplete:function(todoItem){
      todoItem.completed = !todoItem.completed;
      //로컬 스토리지에 데이터를 갱신
      localStorage.removeItem(todoItem.item);
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem));

    }
  }
}
</script>

<style scoped>
ul {
  list-style-type: none;
  padding-left: 0;
  margin-top: 0;
  text-align: left;
}
li {
  display: flex;
  min-height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  border-radius: 5px;
  background: white;
}
.checkBtn {
  line-height: 45px;
  color: #62acde;
  margin-right: 5px;
}
.checkBtnCompleted {
  color: #b3adad;
}
.textCompleted {
  text-decoration: line-through;
  color: #b3adad;
}
.removeBtn {
  margin-left: auto;
  color: #de4343;
}

/*리스트 아이템 트랜지션 효과*/
.list-enter-active, .list-leave-active {
  transition: all 1s;
}
.list-enter, .list-leave-to /* .list-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: translateY(30px);
}
</style>