<template>
  <div id="app">
    <div class="todo-container">
      <div class="todo-wrap">
        <TodoHeader @addTodo="addTodo" />
        <TodoMain :list="list" :changeTodo="changeTodo" :deleteTodo="deleteTodo" />
        <TodoFooter :list="list" @selectTodo="selectTodo" @cleardoneTodo="cleardoneTodo" />
      </div>
    </div>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoMain from './components/TodoMain.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  name: 'App',
  components: {
    TodoHeader,
    TodoMain,
    TodoFooter
  },
  data() {
    return {
      list: JSON.parse(localStorage.getItem('list')) || []
    }
  },
  methods: {
    addTodo(obj){
      // console.log(obj)
      this.list.unshift(obj)
    },
    changeTodo(id){
      // console.log(id)
      this.list.forEach((e)=>{
        if(e.id===id){
          return e.done = !e.done
        }
      })
    },
    deleteTodo(id){
      this.list = this.list.filter((e)=>{
        return e.id !== id
      })
    },
    selectTodo(option){
      this.list.forEach(element => {
        element.done = option
      });
    },
    cleardoneTodo(){
      this.list = this.list.filter(element => {
        return !element.done
      });
    }
  },
  watch:{
    list:{
      handler(val){
        localStorage.setItem('list',JSON.stringify(val))
      },
      deep:true
    }
  }
}
</script>

<style>
  /*base*/
  body {
    background: #fff;
  }

  .btn {
    display: inline-block;
    padding: 4px 12px;
    margin-bottom: 0;
    font-size: 14px;
    line-height: 20px;
    text-align: center;
    vertical-align: middle;
    cursor: pointer;
    box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.05);
    border-radius: 4px;
  }

  .btn-danger {
    color: #fff;
    background-color: #da4f49;
    border: 1px solid #bd362f;
  }

  .btn-danger:hover {
    color: #fff;
    background-color: #bd362f;
  }

  .btn:focus {
    outline: none;
  }

  .todo-container {
    width: 600px;
    margin: 0 auto;
  }
  .todo-container .todo-wrap {
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
  }

</style>
