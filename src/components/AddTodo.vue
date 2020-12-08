<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add todo">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo (e) {
            e.preventDefault();
            const newTodo = {
                // id: Math.random()*1000,  //the api gives it an id now
                title: this.title,
                complete: false
            }
            // send up to parent
            this.$emit('add-todo', newTodo);
            this.title = '';
        }
    }
}
</script>