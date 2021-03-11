<template>
<div>
<div class="flex bg-white shadow-md mt-6 rounded-lg">
    <page :page="pages[index]" class="w-1/2 border-r border-gray-200" ></page>
    <page :page="pages[index+1]" class="w-1/2"></page>
</div>
  <div class="mt-12 flex justify-between ">
    <nav-button @click="decreaseIndex()"> 
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M11 15l-3-3m0 0l3-3m-3 3h8M3 12a9 9 0 1118 0 9 9 0 01-18 0z" />
        </svg>
    </nav-button>
    <nav-button @click="increaseIndex()">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 9l3 3m0 0l-3 3m3-3H8m13 0a9 9 0 11-18 0 9 9 0 0118 0z" />
        </svg>
    </nav-button>
  </div>
</div>
</template>

<script>
import NavButton from './NavButton.vue'
import Page from './Page.vue'

export default {
    name: 'Book',
    props:['pages'],
    components: { Page, NavButton },
    data(){
        return {
            index:0,
        }
    },
    methods: { 
        increaseIndex(){
            if(this.pages.length % 2 === 0){
                if(this.index + 2 < this.pages.length){
                    this.index += 2
                }
            } else {
                if(this.index + 2 < this.pages.length + 1){
                    this.index += 2
                }
            }
        },
        decreaseIndex(){
            if(this.index >= 2){
            this.index -=2
            }
        }
    },
}
</script>
