<template>
  <h1>{{ title }}</h1>
  <input type="text" ref="name">
  <button @click="handleClick">Click Me</button>
  <Modal />
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: { Modal },
  data() {
    return {
      title: 'My First Vue App :)'
    }
  },
  methods: {
    handleClick() {
      //console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      // To focus on this field in DOM
      this.$refs.name.focus()
    }
  }
}
</script>

<style>
/* these styles are global, unless use scoped, but then it will break the #app style */
/* to apply global styles, cna use global.css */
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
