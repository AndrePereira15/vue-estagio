<template>
    <button @click="addEvents()" 
    :style="{background:color}" 
    class="btn">{{text}}</button>
</template>

<script>
export default {
    name: 'Button',
    props:{
        text: String,
        color: String,
    },
    methods: {
        addEvents(){
            this.$emit('showTask')
        },
    },
}
</script>