<template>
  <div class="about">
    <h2>This is the {{ app }} app v{{ version }}.0.0</h2>
    <p :hidden="hideAuthor">written by {{ author }}</p>
    <v-btn :disabled="disabled" @[argument]="showAuthor"
      >{{ authorBtnLabel }} Author</v-btn
    >
    <v-spacer></v-spacer>
    <br />
    <v-btn :disabled="disabled" @[argument]="upgrade" v-if="version < 20"
      >Upgrade to v{{ version + 1 }}.0.0</v-btn
    >
    <v-spacer></v-spacer>
    <br />
    <v-btn @click="enable">{{ toggleLabel }} buttons</v-btn>
    <v-spacer></v-spacer>
    <p>time is: {{ Date.now() }}</p>
    <v-form @submit.prevent="setAuthor(name)">
      <v-text-field label="Enter your name" type="text" v-model="name" />
      <v-btn type="submit">Submit</v-btn>
    </v-form>
  </div>
</template>

<script>
const f = () => console.log('hello')
export default {
  // name: 'About',
  methods: {
    f,
    showAuthor() {
      this.hideAuthor = !this.hideAuthor
      this.hideAuthor
        ? (this.authorBtnLabel = 'show')
        : (this.authorBtnLabel = 'hide')
      // event.target.disabled = true
    },
    enable() {
      this.disabled = !this.disabled
      this.disabled
        ? (this.toggleLabel = 'enable')
        : (this.toggleLabel = 'disable')
    },
    upgrade() {
      this.version++
    },
    setAuthor(newName) {
      this.author = newName
    }
  },
  computed: {
    //cached based on reactive deps so doesn't have to run functions each time called
    // now () {
    //   return Date.now() //wont update bc not reactive dep
    // }
    author: {
      get() {
        return this.firstName + ' ' + this.lastName
      },
      set(newValue) {
        let names = newValue.split(' ')
        this.firstName = names[0]
        this.lastName = names[names.length - 1]
      }
    }
  },
  data() {
    return {
      version: 1,
      app: 'TodoList',
      firstName: 'Michael',
      lastName: 'Wilson',
      hideAuthor: true,
      argument: 'click',
      disabled: false,
      toggleLabel: 'disable',
      authorBtnLabel: 'show',
      name: ''
    }
  }
}
</script>
