<template>
<div class="max-w-2xl mx-auto">
  <div class="mt-12 flex justify-between ">
    <h1 class="text-xl">Mon livre</h1>
    <button class="bg-purple-500 hover:bg-purple-600 text-white rounded py-1 px-2" @click="modal = true" > add page</button>
    <modal @created="refetch()" @close="modal = false" v-if="modal"></modal>
  </div>
    <book :pages="pages"></book>
</div>
</template>

<script>
import axios from "axios"
import Book from './components/Book.vue'
import Modal from './components/Modal.vue'

export default {
  components: { Book, Modal },
  name: 'App',
  data(){
    return {
      pages : [],
      modal:false,
    }
  },
    created(){
        axios
          .get('http://localhost:3000/pages')
          .then(response => (this.pages = response.data))
    },
    methods:{
      refetch(){
        axios
          .get('http://localhost:3000/pages')
          .then(response => (this.pages = response.data))
      }
    }
}
</script>


