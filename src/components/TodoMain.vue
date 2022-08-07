<template>
    <ul class="todo-main">
          <TodoItem 
          v-for="listobj in list" 
          :key="listobj.id" 
          :list="listobj" 
          :changeTodo="changeTodo" 
          :deleteTodo="deleteTodo"
          />
    </ul>
</template>

<script>
    import TodoItem from './TodoItem.vue'
    export default {
        name:'TodoMain',
        components:{
            TodoItem
        },
        props:['list','changeTodo','deleteTodo']
    }
</script>

<style>
    /*main*/
    .todo-main {
    margin-left: 0px;
    border: 1px solid #ddd;
    border-radius: 2px;
    padding: 0px;
    }

    .todo-empty {
    height: 40px;
    line-height: 40px;
    border: 1px solid #ddd;
    border-radius: 2px;
    padding-left: 5px;
    margin-top: 10px;
    }
</style>