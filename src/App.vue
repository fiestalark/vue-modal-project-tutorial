<template>
  <h1>{{ title }}</h1>
  <p>Welcome</p>
  <input type="text" ref="name">
  <button @click="handleClick">Click Me</button>
  <br>
  <br>
  <div v-if="showModal">
    <Modal header="Header string" :header2="header2" :text="text" :theme="theme" @close="toggleModal">
      <template v-slot:links>
        <a href="#">Sign up Now</a>
        <a href="#">More info</a>
      </template>
      <!--Default content only shows if dont pass anything in the slot-->
      <h1>Heading 1 via Slot</h1>
      <p>Paragraph via Slot</p>
    </Modal>
  </div>
  <button @click.shift="toggleModal">Shift Open Modal</button>
  
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: { Modal },
  data() {
    return {
      title: 'My First Vue App :)',
      header2: "Header Too",
      text: 'string two',
      theme: 'sale',
      showModal: false
    }
  },
  methods: {
    handleClick() {
      //console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      // To focus on this field in DOM
      this.$refs.name.focus()
    },
    toggleModal() {
      this.showModal = !this.showModal
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
