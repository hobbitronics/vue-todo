<template>
  <v-container>
    <v-row justify="center">
      <v-col cols="6">
        <v-form @submit="addTodo">
          <v-text-field
            outlined
            type="text"
            v-model="title"
            name="title"
            placeholder="Add todo"
            class="todoInput "
          />
          <v-btn type="submit" value="Submit">Add Todo</v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'AddTodo',
  data() {
    return {
      title: ''
    }
  },
  methods: {
    addTodo(e) {
      e.preventDefault()
      const newTodo = {
        title: this.title,
        completed: false
      }
      // send up to parent
      this.$emit('add-todo', newTodo)
      this.title = ''
    }
  }
}
</script>

<style>
.todoInput {
  max-width: 50ch;
}
</style>
