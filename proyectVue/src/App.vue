<script setup>
import { ref } from 'vue';


let newTask = ref('')

let taskList = ref([{text: 'Estudiar', done: false},
                    {text: 'Jugar', done: true}])

function addTask(){
    if(newTask.value.trim()== '') return
    taskList.value.push({text: newTask.value, done:false})
    newTask.value = ''
}

function setDone(index){
    taskList.value[index].done = !taskList.value[index].done
   
}
function deleteTask(index){
    taskList.value.splice(index,1)
}
</script>

<template>
    <div class="card">
        <h1>Lista de cosas</h1>
        <p class="subtitle">{{ newTask }}</p>
        <div class="a">
            <div v-for="(task,index) in taskList" :key="index" class="task" :class="{done: task.done}">{{ task.text }}  <span  @dblclick="deleteTask(index)" @click="setDone(index)" class="button">x</span></div>
        </div>
        <div>
            <input v-model="newTask" @keypress.enter="addTask" type="text" placeholder="Escribe tu tarea">
            <p class="help" v-show = "newTask != ''"> Presiona enter para confirmar</p>
        </div>
    </div>
</template>

<style scoped>

.done{
    text-decoration: line-through;
    background-color: aliceblue !important;
}


.card{

    background-color: #fbc2b5;
    max-width: 520px;
    border-radius: 8px;
    padding: 18px 16px;
    margin: 0 auto;
    overflow: hidden;
    
}

*{
font-family: Agbalumo;
box-sizing: border-box;
}

h1{
    text-transform: uppercase;
    text-align: center;
    margin: 0;
    font-size: 24px;
}

.subtitle{
    padding: 0;
    margin: 0;
    text-align: center;
    opacity: 0.6;
}

.task{
    display: flex;
    justify-content: space-between;
    background-color: #A14A76;
    border-radius: 2px;
    padding: 2px 8px;
    margin-bottom: 8px;
    margin-top: 4px;
    padding-right: 2px;
    margin-bottom: 2px;


}

.task:hover{
    background-color: #CDB2AB;
}

.button{
    display: inline-flex;
    align-items: center;
    background-color: #FBC2B5 ;
    padding: 0 6px;
    border-radius: 2px;
    color: white;
    
}

.button:hover{
    cursor: pointer;
    background-color: #F786AA;
}

input{
    width: 100%;
    box-sizing: border-box;
    border: none;
    padding: 4px 4px;
    margin-top: 4px;
    border-radius: 6px;
}

.help{
    margin: 0;
    font-size: 12px;
    opacity: 0.4;
}






 

</style>
