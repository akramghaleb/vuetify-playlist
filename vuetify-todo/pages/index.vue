<template>
  <div class="home pa-6">
    <v-text-field 
      v-model="newTaskTitle"
      @click:append="addTask()"
      @keyup.enter="addTask()"
      class="pa-3"
      outlined label="Add Task"
      hide-details
      clearable 
      append-icon="mdi-plus"></v-text-field>
    <v-list lines="three" select-strategy="classic">
      <v-list-subheader>Tasks</v-list-subheader>

      <div v-for="task in tasks" :key="task.id" >
        <v-list-item 
          :value="task.name"
           @click="changeTask(task.id)"
           :class="{ 'bg-blue-lighten-5' : task.done }"
           >
          <template v-slot:prepend>
            <v-list-item-action start>
              <v-checkbox-btn :model-value="task.done"></v-checkbox-btn>
            </v-list-item-action>
          </template>

          <v-list-item-title
          :class="{ 'text-decoration-line-through' : task.done }"
          >{{ task.name }}</v-list-item-title>

          <v-list-item-subtitle>
            {{ task.description }}
          </v-list-item-subtitle>
          
          <template v-slot:append>
            <v-btn @click.stop="deleteTask(task.id)"
              color="blue"
              icon="mdi-delete"
              variant="text"
            ></v-btn>
          </template>
        </v-list-item>
        <v-divider></v-divider>
      </div>
    </v-list>
  </div>
</template>

<script setup>

const newTaskTitle = ref('');
const tasks = ref([]);

onMounted(()=>{
  tasks.value = JSON.parse(localStorage.getItem('tasks') ?? '[]');
});

const addTask = ()=>{
  if(newTaskTitle.value != ''){
    let newTask = {
      id : Date.now(),
      name: newTaskTitle.value,
      description : '',
      done : false
    }

    tasks.value.push(newTask);
    newTaskTitle.value = ''

    localStorage.setItem('tasks' ,JSON.stringify(tasks.value));
  }
  
}

const changeTask = (id) => {
  let task = tasks.value.filter(task => task.id === id)[0];
  task.done = !task.done;
  localStorage.setItem('tasks' ,JSON.stringify(tasks.value));
};

const deleteTask = (id) => {
  tasks.value = tasks.value.filter(task => task.id !== id);
  localStorage.setItem('tasks' ,JSON.stringify(tasks.value));
}
</script>
