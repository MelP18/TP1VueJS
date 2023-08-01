<template>
    <div class="block">
        <div class="register">
            <div class="form__head">
                <h2>TO-DO-LIST</h2>
            </div>
            <div class="form__middle" v-for="element in TaskList" :class="element.is_finished ? 'active' : ''">
                <!-- <div :class="element.is_finished ? 'active' : ''"> -->
                    <div v-if='element.is_finished' class="task">
                        <h4 class="bar">{{ element.name }}</h4>
                        <input v-bind:checked='element.is_finished' type="checkbox">
                    </div>
                    <div v-else class="task">
                        <h4>{{ element.name }}</h4>
                        <input v-bind:checked='element.is_finished' type="checkbox">
                    </div>

               <!--  </div> -->
                

            </div>
            <div class="taskModal">
                <span @click="closeTaskModal"></span>
                <label for="" class="name__of__task">Nom de la tâche</label>
                <input type="text">
                <button @click="addTask">Ajouter</button>
            </div>
            <div class="form__bottom">
                <button @click="openTaskModal">
                    {{ add }}
                </button>
            </div>

        </div>
    </div>
</template>


/*===========================================+++ SCRIPT JS ++=============================================*/
<script lang="ts" setup>
import { ref } from 'vue'
//const count = ref(0)

const add = ref('Ajouter une tache')

function openTaskModal(){
let  task = document.querySelector('.taskModal')
 if(task){
    task.classList.add('active')
 }
}
function closeTaskModal(){
    let  task = document.querySelector('.taskModal')
    let  close = document.querySelector('.taskModal span')
    if(close){
        if(task){
            task.classList.remove('active')
        }
    }
}

function addTask (){
    let formMiddle = document.querySelector('.form__middle')
    if(formMiddle){
        let input = document.querySelector('.taskModal input')
        if(input){
            const inputValue = input.value
            const  lineTask = 
                `
                    <div class="task">
                        <h4>${inputValue}</h4>
                        <input v-bind:checked='element.is_finished' type="checkbox">
                    </div>
                `
            formMiddle.innerHTML += lineTask

            const  lineTaskList = 
                {
                name: inputValue,
                is_finished: false
            }
            TaskList.push(lineTaskList)
            console.log(lineTaskList);
        }
    }
   
   
}
const TaskList = [
    {
        name: 'Lessive',
        is_finished: false
    },
    {
        name: 'Achat',
        is_finished: true
    },
    {
        name: 'Vente',
        is_finished: false
    },
    {
        name: 'Vaiselle',
        is_finished: false
    },
    {
        name: 'Exercice',
        is_finished: true
    },
]
console.log(TaskList);


</script>


/*===========================================+++ STYLE CSS ++=============================================*/
<style>
* {
    position: relative;
    padding: 0;
    margin: 0;
    z-index: 5;
    box-sizing: border-box;
    font-size: 14px;
    color: black;
}

.block {
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: rgb(86, 2, 2);
}

.block .register {
    width: 40%;
    border: 1px solid white;
    background-color: rgb(72, 71, 71);
    padding: 15px;
    display: flex;
    flex-direction: column;
    gap: 25px;
    box-shadow: 0px 0px 5px;
}

.form__middle {
    display: flex;
    flex-direction: column;
    gap: 25px;
}

.form__head h2 {
    font-weight: bold;
    font-size: 25px;
    white-space: nowrap;
    text-align: center;
    color: white;
}

.task {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border: 1px solid white;
    padding: 10px;
}

.task h4 {
    color: white;
    font-weight: bold;
    font-size: 17px;
}

.task input {
    width: 20px;
}
.active {
   background-color: white;
   .task h4 {
    color: black
    }
}

.bar {
    text-decoration: line-through;
}

.form__bottom {
    display: flex;
    justify-content: center;
}

.form__bottom button {
    cursor: pointer;
    padding: 10px 25px;
    border-radius: 9px;
    border: none;
}
.taskModal{
    width: 100%;
    height:100%;
    position: fixed;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #550101b5;
    z-index:6;
    border: 2px solid black;
    top:50%;
    left: 50%;
    transform: translate(-50%,-50%) scale(0) ;
    opacity: 0;
    visibility: hidden;
    transition: 1s;
}
.taskModal.active{
    visibility: visible;
    opacity: 1;
    transform: translate(-50%, -50%) scale(1);
}

.taskModal span{
    position: absolute; 
    display: block;
    width: 35px;
    height: 35px;
    background-color: black;
    top: 30px;
    right: 30px;
}

.taskModal span::after, .taskModal span::before{
    content: '';
    width: 30px;
    height: 4px;
    background-color: #fff;
    position: absolute;
    top: 50%;
    left: 50%; 

}
.taskModal span::after{
    transform: translate(-50%, -50%) rotate(-45deg);
}

.taskModal span::before{
    transform: translate(-50%, -50%) rotate(45deg);
} 
</style>