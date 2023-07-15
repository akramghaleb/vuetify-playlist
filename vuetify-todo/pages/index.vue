<template>
  <div class="home pa-6">
    <v-list lines="three" select-strategy="classic">
      <v-list-subheader>Tasks</v-list-subheader>

      <div v-for="task in tasks" :key="task.id" >
        <v-list-item :value="task.name" @click="task.done = !task.done">
          <template v-slot:prepend="{ isActive }">

            <v-list-item-action start>
              <v-checkbox-btn :model-value="task.done"></v-checkbox-btn>
            </v-list-item-action>
          </template>

          <v-list-item-title>{{ task.name }}</v-list-item-title>

          <v-list-item-subtitle>
            {{ task.description }}
          </v-list-item-subtitle>
        </v-list-item>
        <v-divider></v-divider>
      </div>
    </v-list>
  </div>
</template>

<script setup>

const tasks = ref([
  {id:1 , name:'Get Up' , description:'', done:false},
  {id:2 , name:'Get Banana' , description:'', done:false},
  {id:3 , name:'Eat Banana' , description:'', done:false},
]);
</script>
