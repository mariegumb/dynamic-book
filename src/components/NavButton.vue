<template>
<div>
    <button class="h-12 w-12 text-gray-500 " @click="$emit('click')">
        <slot></slot>
    </button>
</div>
</template>

<script>
export default {
    name: 'NavButton',
    props:['page']
}
</script>
