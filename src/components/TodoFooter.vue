<template>
    <div class="todo-footer" v-if="total">
          <label>
            <input type="checkbox" :checked="isall" v-model="isall" />
          </label>
          <span>
            <span>已完成{{totaldone}}</span> / 全部{{total}}
          </span>
          <button class="btn btn-danger" @click="cleardonelist" >清除已完成任务</button>
    </div>
</template>

<script>
    export default {
        name:'TodoFooter',
        // props:['list','selectTodo','cleardoneTodo'],
        props:['list'],
        computed:{
          totaldone(){
            let i = 0
            this.list.forEach(element => {
              if(element.done === true){
                i++
              }
            });
            return i
          },
          total(){
            return this.list.length 
          },
          isall:{
            get(){
              return this.total === this.totaldone && this.total > 0
            },
            set(val){
              this.$emit('selectTodo',val)
            }
          }
        },
        methods: {
          cleardonelist(){
            this.$emit('cleardoneTodo');
          }
        },
    }
</script>

<style>
    /*footer*/
    .todo-footer {
    height: 40px;
    line-height: 40px;
    padding-left: 6px;
    margin-top: 5px;
    }

    .todo-footer label {
    display: inline-block;
    margin-right: 20px;
    cursor: pointer;
    }

    .todo-footer label input {
    position: relative;
    top: -1px;
    vertical-align: middle;
    margin-right: 5px;
    }

    .todo-footer button {
    float: right;
    margin-top: 5px;
    }
</style>