<template>
<div @dblclick="$emit('toggleReminder', task.id)"
    :class="[task.reminder ? 'reminder' : '', 'task']">
    <h3>{{task.text}}
        <i @click="$emit('delete', task.id)" 
        class="fas fa-ban"></i>
    </h3>
    <p>{{task.day}}</p>
</div>
</template>

<script>
export default {
    name:'Task',
    props:{
        task: Object
    },
}
</script>

<style scope>
.fas{
    color: rgb(255, 67, 67)
}
.task{
    background: rgb(118, 182, 201);
    margin: 15px;
    padding: 1px 10px;
    cursor: pointer;
    border: 2px solid blue;
}
.task.reminder{
    border-left: 10px solid green;
}
.task h3{
    font-style: italic;
    display: flex;
    align-items: center;
    justify-content: space-between;
}
</style>