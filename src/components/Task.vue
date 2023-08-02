<template>
    <div v-bind:class="{ 'active bar': element.is_finished }" class="form__middle">
        <div class="task">
            <h4>{{ element.name }}</h4>
            <input v-bind:checked='element.is_finished' v-model="element.is_finished" type="checkbox">
            <StarIcon @click="markAsImportant(element)" class="star" :is_important='element.is_important' />
            <DeleteIcon class="delete" @click="removeElement"/>
        </div>
    </div>
</template>

<script lang="ts" setup>

import StarIcon from "@/components/StarIcon.vue"
import DeleteIcon from "./DeleteIcon.vue";
import {Task} from "@/Types/task"

const emits = defineEmits(['delete'])
const props = defineProps<{ element: Task}>()


function markAsImportant(element: Task) {
    element.is_important = !element.is_important
}

function removeElement(){
    emits('delete',props.element)
}
</script>

<style>

.delete{
    width: 15px;
    cursor: pointer;
}
</style>