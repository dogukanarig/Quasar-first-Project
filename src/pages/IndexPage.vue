<template>
  
  <q-page class="flex flex-center">
    <q-card class="my-card">

      <!-- To-Do List Text -->
      <q-card-section>
        <div class="text-h4 text-center" style="width: 600px">
          To-Do List
        </div>
      </q-card-section>

      <!-- Add TodoTask -->
      <q-card-section>
        <div class="row justify-center">
          <div class="col-12 q-pb-md">
            <q-input v-model="todoTask" label="Input Task" clearable label-color="red" standout="text-red" >
              <template v-slot:after>
                <q-btn round dense flat icon="send" @click="addItem" />
              </template>
            </q-input>
          </div>
        </div>
      </q-card-section>

      
      <!-- To-Do list items -->
      <q-card-section v-if="todoList.length > 0">
        <div class="row justify-center" v-for="(item, index) in todoList" :key="index">
          <div class="col-8 q-py-md">
            {{ item.value }}
            
          </div>

          <div class="col-auto q-py-md">
            <q-btn round dense flat icon="done" @click="removeItem(index)" />
          </div>
        </div>
      </q-card-section>

      <!-- No item found -->
      <q-card-section v-else>
        <div class="row justify-center">
          <div class="col-12">
            <div class="text-h6">
              No items in the list
            </div>
          </div>
        </div>
      </q-card-section>



    </q-card>
  </q-page>
</template>



<script setup>
import { ref } from 'vue'

const todoList = ref([
  { value: "Create an app" },
  { value: "Build an app" },
]);

const todoTask = ref("");
const addItem = () => {
  todoList.value.push({ value: todoTask.value })
}

const removeItem = (index) => {
    
    todoList.value.splice(index,1);
}


</script>

