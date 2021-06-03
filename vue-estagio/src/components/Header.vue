<template>
    <header>
        <h1>{{title}}</h1>
        <Button @showTask="$emit('showTask')"
        :text ="showAllAddTasks ? 'Close' : 'Add Task'" 
        :color="showAllAddTasks ? 'red' : 'green'"/>
    </header>
</template>

<script>
import Button from './Button'

export default {
    name: 'Header',
    props: {
        title: String,
        showAllAddTasks: Boolean,
    },
    components: {
        Button
    },
    emits: ['showTask']
}
</script>

<style scoped>
header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}
</style>