<template>
  <div class="ListTasks">
    <v-text-field clearable label="Add task"
    
    v-model="task.title"
    @keyup.enter.exact="addNewTask"
    ></v-text-field>
    <v-list lines="three" select-strategy="classic">

      <v-list-item v-for="(task, index) in tasks"
       :key="index"
       :value="index">
        <template v-slot:prepend="{ isActive }">

          <v-list-item-action start>
            <v-checkbox-btn :model-value="isActive"></v-checkbox-btn>
          </v-list-item-action>
        </template>

        <v-list-item-title>{{ task.title }}</v-list-item-title>

        <v-list-item-subtitle>
         {{ task.description }}
        </v-list-item-subtitle>
      </v-list-item>

    </v-list>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const task = ref({
  title:"",
  desciption:""
})

const tasks = ref([
  {
    title:"Estudar",
    description:" estudar documentação do vuetify"
  }
])

const addNewTask = ()=>{
  tasks.value.push({
    title: task.value.title,
    description: task.value.description
  })

  task.value = {
    title:"",
    description:""
  }
}
</script>

<style>

</style>