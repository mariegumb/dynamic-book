<template>
    <div class="h-96 p-6 w-full" v-if="page">
        <span v-if="page.text !== ''">{{page.text}}</span>
        <div v-else-if="page.image !== ''" class="bg-cover mx-auto mt-6 inline-block h-48 w-48 rounded-full" :style="'background-image: url(' + page.image + ')'">
        </div>
    </div>
</template>

<script>
export default {
    name: 'Page',
    props:['page']
}
</script>
