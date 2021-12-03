<template>
    <div>
        <h1>Minha lista de tarefas!</h1>
        <button @click="handleShowHideList">
        Mostrar a lista
        </button>
        <br>
        <br>
        <input type="text" v-focus>
      
      <ul v-if="showList">
         <li
            v-for="(task, index) in tasks"
            @dblclick="complete(task)"
            :key="`${task}-${index}`"
         >
         {{ task.name }}
        <button
        @click="remove(task)"
        >&times;</button>
        </li>
      </ul>
      <p v-else>Lista de tarefas escondidas</p>
    </div>
</template>

<script>
const focus = {
    inserted: (el) => {
        el.focus()
    }
}
export default {
    directives: {
        focus,
    },
    data:() => ({
        showList: false,
        tasks:[
            { name: 'Fazer o curso', isDone: false }
        ]   
    }),
    methods: {
        handleShowHideList(){
            this.showList = !this.showList
        },
        remove(task){
            this.tasks = this.tasks.filter(t => t.name !== task.name)
        }
    }
}
</script>
