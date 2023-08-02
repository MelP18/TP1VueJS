<template>
    <div class="block">
        <div class="register">
            <div class="form__head">
                <h2>TO-DO-LIST</h2>
            </div>
            <task @delete="deleteTask" v-for=" element in TaskList" :element="element" />
            <div>
                <label>Nom de la tâche</label>
                <input type="text" v-model="task">
                <Btn @click="addTask" />
            </div>
            <!-- <div class="taskModal">
                <span></span> 
                <label>Nom de la tâche</label>
                <input type="text" v-model="task">
               <button @click="addTask">Ajouter</button> 
            </div> -->

            <!-- <div>{{ line }}</div>  -->
             <div class="form__bottom">
                <button @click="">
                    {{ add }}
                </button>
            </div> 

        </div>
    </div>
</template>


/*===========================================+++ SCRIPT JS ++=============================================*/
<script lang="ts" setup>

import Task from "@/components/Task.vue"
import Btn from "@/components/Btn.vue"
import { ref } from 'vue'
//const count = ref(0)
const task = ref('')
const add = ref('Ajouter une tache')

function deleteTask(element) {
    console.log(element);
    const index = TaskList.value.findIndex((item) => item.name == element.name)
    if (index >= 0) {
        TaskList.value.splice(index, 1)
    }
    console.log(index);


}

const addTask = () => {
    TaskList.value.push({
        name: task.value,
        is_finished: false
    }),
        task.value = ''
}
/* function markAsImportant(element) {
    element.is_important = !element.is_important
} */
console.log(addTask);

const TaskList = ref([
    {
        name: 'Lessive',
        is_finished: false,
        is_important: false

    },
    {
        name: 'Achat',
        is_finished: false,
        is_important: true
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
        is_finished: false
    },
])
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
    width: 35%;
    height: 460px;
    border: 1px solid white;
    background-color: rgb(15, 15, 15);
    padding: 15px;
    display: flex;
    flex-direction: column;
    gap: 25px;
    box-shadow: 0px 0px 5px;
    overflow-y: scroll;
}

.block .register::-webkit-scrollbar {
    width: 5px;
}

.block .register::-webkit-scrollbar-thumb {
    background-color: rgb(142, 20, 20);
    border-radius: 20px;
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
    cursor: pointer;
    width: 15px;
    height: 15px;

}

.active {
    /*  border: 1px solid rgb(88, 221, 31); */
    background-color: rgb(120, 3, 3);

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

/* .taskModal {
    width: 100%;
    height: 100%;
    position: fixed;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #550101b5;
    z-index: 6;
    border: 2px solid black;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) scale(0) ;
    opacity: 0;
    visibility: hidden;
    transition: 1s;
}

.taskModal.active {
    visibility: visible;
    opacity: 1;
    transform: translate(-50%, -50%) scale(1);
}

.taskModal span {
    position: absolute;
    display: block;
    width: 35px;
    height: 35px;
    background-color: black;
    top: 30px;
    right: 30px;
}

.taskModal span::after,
.taskModal span::before {
    content: '';
    width: 30px;
    height: 4px;
    background-color: #fff;
    position: absolute;
    top: 50%;
    left: 50%;

}

.taskModal span::after {
    transform: translate(-50%, -50%) rotate(-45deg);
}

.taskModal span::before { 
    transform: translate(-50%, -50%) rotate(45deg);
}*/
.star {
    width: 15px;
    cursor: pointer;
}

.task p {
    cursor: pointer;
}
</style>