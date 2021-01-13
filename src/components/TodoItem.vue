<template>
  <v-container>
    <v-row justify="space-between">
      <v-checkbox
        v-model="completed"
        :id="toString(todo.id)"
        type="checkbox"
        @click="$emit('complete', todo.id)"
      />
      <span :class="{ 'is-complete': todo.completed }">{{ todo.title }}</span>
      <v-btn
        icon
        elevation="2"
        @click="$emit('del-todo', todo.id)"
        class="red float-right"
        >x</v-btn
      >
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'TodoItem',
  props: ['todo'],
  data() {
    return {
      completed: this.todo.completed
    }
  }
}
</script>

<style scoped>
.is-complete {
  text-decoration: line-through;
}
span {
  padding-left: 1rem;
}
</style>
