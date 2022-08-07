<template>
  <div class="todo-header">
    <input
      type="text"
      placeholder="輸入待辦事項，Enter確定"
      v-model="myinput"
      @keyup.enter="addlist"
    />
  </div>
</template>

<script>
//nanoid自動生成uuid
import { nanoid } from "nanoid";
export default {
  name: "TodoHeader",
  data() {
    return {
      myinput: "",
    };
  },
  // props:['addTodo'],
  methods: {
    addlist() {
      // this.addTodo({id:nanoid(),need:this.myinput,done:false});
      const todoobj = { id: nanoid(), need: this.myinput, done: false };
      this.$emit("addTodo", todoobj);
      this.myinput = "";
    },
  },
};
</script>

<style scoped>
/*header*/
.todo-header input {
  width: 560px;
  height: 28px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 4px 7px;
}

.todo-header input:focus {
  outline: none;
  border-color: rgba(82, 168, 236, 0.8);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075),
    0 0 8px rgba(82, 168, 236, 0.6);
}
</style>
