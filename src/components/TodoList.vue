<script setup>
  import { computed, defineProps } from 'vue';

  const props = defineProps(['tarefas']);

  // Verifica se todas as tarefas estão finalizadas
  const todasFinalizadas = computed(() => {
    return props.tarefas.length > 0 && props.tarefas.every(tarefa => tarefa.finalizada);
  });

  const deletarTarefa = (index) => {
    props.tarefas.splice(index, 1);
  };
</script>

<template>
  <div>
    <template v-if="tarefas.length > 0">
      <div class="container">
        <p class="mt-4" v-if="todasFinalizadas">Todas as tarefas estão finalizadas.</p>
      </div>
      <ul class="list-group mt-4">
        <li v-for="(tarefa, index) in tarefas" :key="tarefa.titulo" class="list-group-item">
          <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada" :id="tarefa.titulo" type="checkbox">
          <button @click="deletarTarefa(index)" class="btn btn-danger ms-3">
            <i class="bi bi-trash3"></i>
          </button>
          <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">{{ tarefa.titulo }}</label>
        </li>
      </ul>
    </template>
  </div>
</template>

<style scoped>
  .done {
    text-decoration: line-through;
  }
</style>
