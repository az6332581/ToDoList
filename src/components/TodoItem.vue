<template>
  <li>
      <label>
        <input type="checkbox" :checked=list.done @change="changelist(list.id)"/>
        <span>{{list.need}}</span>
      </label>
      <button class="btn btn-danger" @click="deletelist(list.id)">删除</button>            
  </li>
</template>

<script>
    export default {
        name:'TodoItem',
        props:['list','changeTodo','deleteTodo'],
        methods: {
          changelist(id){
            this.changeTodo(id);
          },
          deletelist(id){
            this.deleteTodo(id)
          }
        }
    }
</script>

<style scoped>
  /*item*/
  li {
    list-style: none;
    height: 36px;
    line-height: 36px;
    padding: 0 5px;
    border-bottom: 1px solid #ddd;
  }

  li label {
    float: left;
    cursor: pointer;
  }

  li label li input {
    vertical-align: middle;
    margin-right: 6px;
    position: relative;
    top: -1px;
  }

  li button {
    float: right;
    display: none;
    margin-top: 3px;
  }

  li button:hover {
    display: block;
  }

  li:before {
    content: initial;
  }

  li:last-child {
    border-bottom: none;
  }

  li:hover {
    background-color: rgb(182, 179, 179);  
  }
  li:hover button{
    display: block;
  }
</style>