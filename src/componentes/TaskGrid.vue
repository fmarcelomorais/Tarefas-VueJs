<template>
    <div class="task-grid">
        <template v-if="tasks.length">
            <Task v-for="(task, id) in tasks" 
                :key="task.name"
                @taskDeleted="$emit('taskDeleted',id)"
                :task="task"
                @taskStateChange="$emit('taskStateChange', id)"
                >
              
            </Task>
        </template>
        <p v-else class="no-task">Quais as Tarefas de Hoje?</p>
    </div>    
</template>

<script>
import Task from './Task.vue'


export default {
    components:{
        Task,
    },
    props:{
        tasks: {
            type: Array,
            required: true
            }
    }
}
</script>

<style scoped>
    .task-grid{
        display: flex;
        justify-content: center;
        flex-wrap: wrap;

    }
    .task-grid .task{
        margin: 10px;
    }
    .no-task{
        color: #AAA;
        font-size: 1.7rem;
    }
</style>