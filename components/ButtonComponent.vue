<template>
  <button type="" v-on:click="taskAction">
    {{action}}
  </button>
</template>

<script lang="ts">

import Vue from 'vue'

export default Vue.extend({
  name: 'ButtonComponent',
  props: {
    action: {
      type: String,
      required: true,
    },
  },
   data(){
    return {
    }
  },
  mounted() {
  },
  methods: {
    taskAction: function() {
      if (this.action == 'Adicionar') {
        this.$emit('Adicionar');
      }
      else if (this.action == 'Finalizar') {
        this.$emit('Finalizar');
      }
      else if (this.action == 'Editar'){
        this.$emit('Editar');
      }
      else if (this.action == 'Salvar'){
        this.$emit('Salvar');
      }
    }
  },
})
</script>

<style>
  .nuxt-logo {
    height: 180px;
  }
  </style>