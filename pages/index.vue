<template>
  <div>
    <h1>to do list</h1>
    <div>
      <input type="text" v-model="task"/>
      <button-component :action="'Adicionar'" v-on:Adicionar="addTask"></button-component>
    </div>
    <div v-if="tasks.length>0">
      <li v-for="(task, index) in tasks" :key="index">
        <div v-if="index != editingTask">
          {{task}}
          <button-component :action="'Editar'" v-on:Editar="editTask(index)"></button-component>
          <button-component :action="'Finalizar'" v-on:Finalizar="removeTask(index)"></button-component>
        </div>
        <div v-if="isEditing == true && index == editingTask">
          <input type="text" v-model="tasks[index]">
          <button-component :action="'Salvar'" v-on:Salvar="saveTask(index)"></button-component>
        </div>
      </li>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexPage',
  data(){
    return {
      task: '',
      tasks: [],
      isEditing: false,
      editingTask: -1,
    }
  },
  mounted() {
  },
  methods: {
    addTask: function() {
      if (this.task != '') {
        this.tasks.push(this.task);
        this.task = '';
      }
    },
    removeTask: function(index: any) {
      this.tasks.splice(index , 1);
    },
    editTask: function(index: any) {
      this.isEditing = true;
      this.editingTask = index;
    },
    saveTask: function(index: any) {
      this.tasks[index] = this.tasks[index];
      this.isEditing = false;
      this.editingTask = -1;
    }
  },
})
</script>

<style>
  input {
    width: 250px;
  }  
</style>