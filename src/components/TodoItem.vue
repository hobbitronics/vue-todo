<template>
    <div class="todo-item" >
        <p>
            <input v-model="todo.completed" :id=todo.id type="checkbox" >
            <span :class="{'is-complete':todo.completed}">{{todo.title}}</span>
            <button @click="$emit('del-todo', todo.id)" class="del">x</button>
        </p>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"]
//     methods: {
//         markComplete () {
//             this.todo.completed = !this.todo.completed
//         }
//     },
//     mounted () {  //fires when mounted to dom
//         const box = document.getElementById(this.todo.id)
//         box.checked = this.todo.completed
//         console.log(box)
//     }
}
</script>

<style scoped>
    .todo-item {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
  }
  .is-complete {
    text-decoration: line-through;
  }
  span {
      padding-left: 1rem;
  }
  .del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }
</style>