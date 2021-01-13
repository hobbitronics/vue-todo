<template>
  <div>
    <div :key="todo.id" v-for="todo in todos">
      <TodoItem
        :todo="todo"
        @del-todo="$emit('del-todo', todo.id)"
        @complete="$emit('complete', todo.id)"
      />
    </div>
  </div>
</template>

<script>
import TodoItem from './TodoItem.vue'

export default {
  name: 'Todos',
  components: {
    TodoItem
  },
  props: ['todos'],
  data() {
    return {}
  }
}
</script>
