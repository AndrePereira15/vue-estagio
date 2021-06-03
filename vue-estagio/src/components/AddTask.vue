<template>
    <form @submit="toSubmit" 
    class= "add-form">
        <div class= "form-control">
            <label>Task</label>
            <input 
            type="text"
            v-model="text"
            name="text" 
            placeholder="Add Event"/>
        </div>
        <div class="form-control">
            <label>Day & Time</label>
            <input 
            type="text" 
            v-model="day"
            name="day" 
            placeholder="Add Day & Hours"/>
        </div>
        <div class="form-control form-control-check">
            <label> Set Reminder </label>
            <input 
            type="checkbox" 
            v-model="reminder"
            name="reminder" />
        </div>
        <input
        type="submit"
        value="Save Task"
        class="btn btn-block" />
    </form>
</template>

<script>
export default {
    name: 'AddTask',
    data(){
        return{
            text: '',
            day: '',
            reminder: false
        }
    },
    methods: {
        toSubmit(e){
            e.preventDefault();
            if(!this.text){
                alert('Please add a task')
                return
            }

            const newTask = {
                id: Math.floor(Math.random()*10000),
                text: this.text,
                day: this.day,
                reminder: this.reminder
            }

            this.$emit('addATask', newTask)
        }
    }
}
</script>

<style scoped>
.add-form{
    margin-bottom: 40px;
}
.form-control{
    font-style: italic;
    font-size: 20px;
    margin: 20px 1px;
}
.form-control label{
    display: block;
}
.form-control input{
    width: 100%;
    height: 30px;
    margin: 1px;
    padding: 1px 3px;
    font-size: 20px;
}
.form-control-check{
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.form-control-check label{
    flex: 1;
}
.form-control-check input{
    flex: 2;
    height: 20px;
}
</style>