<template>
    <div class="taskModal">
        <span></span> 
        <label>Nom de la tâche</label>
        <input type="text" v-model="task">
        <button @click="addTask">Ajouter</button> 
    </div> 
</template>