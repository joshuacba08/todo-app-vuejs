<template>
  <div class="relative bottom-24">
    <InputTask @sendTask="addTask"/>
    <TaskList :tasks="arrayTasks" @changeState="changeTaskState" @clearComplete="clearCompleteTasks" @deleteTask="deleteTaskById" />
  </div>
</template>

<script>
import InputTask from './InputTask.vue';
import TaskList from './TaskList.vue';
export default {
    data() {
        return {
            arrayTasks: []
        };
    },
    methods:{
        addTask(e){
            console.log(e.target.value);
            this.arrayTasks.push({
                id: this.arrayTasks.length + 1,
                state: false,
                date: new Date(),
                description: e.target.value,
            });
        },
        changeTaskState(id){
            const newArrayTask = this.arrayTasks.map(task=>{
                if(task.id === id){
                    task.state = !task.state
                }
                return task;
            });
            this.arrayTasks = newArrayTask;
        },
        clearCompleteTasks(){
            const result = this.arrayTasks.filter( task => task.state !== true);
            this.arrayTasks = result;
        },
        deleteTaskById(id){
            const result = this.arrayTasks.filter( task => task.id !== id);
            this.arrayTasks = result;
        }
    },  
    components: { InputTask, TaskList },
}
</script>

<style>

</style>