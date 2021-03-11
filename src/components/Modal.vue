<template>
<div class="fixed z-10 inset-0 overflow-y-auto">
  <div class="flex items-end justify-center min-h-screen pt-4 px-4 pb-20 text-center sm:block sm:p-0">

    <div class="fixed inset-0 transition-opacity" aria-hidden="true">
      <div class="absolute inset-0 bg-gray-500 opacity-75"></div>
    </div>

    <span class="inline-block sm:align-middle sm:h-screen" aria-hidden="true">&#8203;</span>

    <div class="inline-block align-bottom bg-white rounded-lg px-4 pt-5 pb-4 text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-lg sm:w-full sm:p-6" role="dialog" aria-modal="true" aria-labelledby="modal-headline">
      <div class="block absolute top-0 right-0 pt-4 pr-4">
        <button type="button" @click="$emit('close')" class="bg-white rounded-md text-gray-400 hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-purple-500">
          <span class="sr-only">Close</span>
          <svg class="h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" aria-hidden="true">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
          </svg>
        </button>
      </div>
      <div class="sm:flex sm:items-start">
    
        <div class="mt-3 text-left w-full">
          <h3 class="text-lg leading-6 font-medium text-gray-900" id="modal-headline">
              Créer une nouvelle page 
          </h3>
          <div class="mt-2 " >
            <div v-if="image === ''">
                <label for="text" class="block text-sm font-medium text-gray-700">Texte :</label>
                <div class="mt-1">
                    <textarea v-model="text" type="text" name="text" id="text"  class="shadow-sm h-48 pt-2 pl-3 bg-gray-100 focus:ring-indigo-500 focus:border-purple-500 block w-full sm:text-sm border-gray-300 rounded-md" placeholder="Texte"></textarea>
                </div>
            </div>
            <div class="mt-2 " v-if="text === ''">
                <label for="image" class="block text-sm font-medium text-gray-700">Url de l'image :</label>
                <div class="mt-2 ">
                    <input v-model="image"  type="text" name="image" id="image" class="shadow-sm h-10  pl-3 bg-gray-100 focus:ring-indigo-500 focus:border-purple-500 block w-full sm:text-sm border-gray-300 rounded-md" placeholder="Image">
                </div>
            </div>
          </div>
        </div>
      </div>
      <div class="mt-5 sm:mt-4 sm:flex sm:flex-row-reverse">
        <button @click="create()" type="button" class="w-full inline-flex justify-center rounded-md border border-transparent shadow-sm px-4 py-2 bg-purple-500 text-base font-medium text-white hover:bg-purple-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-purple-500 sm:ml-3 sm:w-auto sm:text-sm">
          Créer
        </button>
        <button @click="$emit('close')" type="button" class="mt-3 w-full inline-flex justify-center rounded-md border border-gray-300 shadow-sm px-4 py-2 bg-white text-base font-medium text-gray-700 hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-purple-500 sm:mt-0 sm:w-auto sm:text-sm">
          Annuler
        </button>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import axios from "axios"

export default {
    name: 'Page',
    props:['page'],
    data(){
      return {
        text: '',
        image: '',
      }
    },
     methods: { 
        create(){
          const newPage = {text : this.text, image : this.image}
          axios.post('http://localhost:3000/pages', newPage).then(() => {
            this.text = ''
            this.image = ''
            this.$emit('created')
            this.$emit('close')
          })
        }
    },
}
</script>
