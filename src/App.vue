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
  <div v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <h1>This is a different Modal</h1>
      <p>Very different</p>
      <template v-slot:links>
        <a href="https://www.google.com/search?client=firefox-b-d&sca_esv=f377f8634278135a&sxsrf=ADLYWIKCbnB0HhgEvhdnyO36ovmnw28_Rw:1729293680659&q=puppies&udm=2&fbs=AEQNm0CFDpRHaDHkXm_YXueHTfHtrgIXUKlluACpCix4T5ZoUSz6e3GWv4zN_09JkP2cR-DwqD-ER1CSuTjXzdXNKT0Wma9mNyum3oWLzhs1xt8u5N_8f3uUgStDs9UpKFAFlFGSOMoqQM9HMiNsP9mioHh2RXyquw6CV17dtB6pod7Wqwuaoj8KLwF-5ybcxBC-9vVePghwqzsfsWfHCa5dRS4yxLs8KA&sa=X&ved=2ahUKEwi_7rD8iJmJAxX2mIkEHcfmBUUQtKgLegQIFBAB&biw=1920&bih=941&dpr=1" target="_blank"> Puppies!</a>
      </template>
    </Modal>
  </div>
  <button @click.shift="toggleModal">Shift Open Modal</button>
  <button @click="toggleModalTwo">Open Modal 2</button>
  
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
      showModal: false,
      showModalTwo: false
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
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
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
