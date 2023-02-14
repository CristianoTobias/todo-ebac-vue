<script setup>
const props = defineProps(["tarefas", "tarefasPendentes"]);
</script>

<template>
  <ul class="list-group mt-4">
    <li class="list-group-item" v-for="tarefa in props.tarefas">
      <input
        @change="(evento) => (tarefa.finalizada = evento.target.checked)"
        :checked="tarefa.finalizada"
        type="checkbox"
        :id="tarefa.titulo"
      />
      <label
        :class="{ done: tarefa.finalizada }"
        :for="tarefa.titulo"
        class="ms-3"
      >
        {{ tarefa.titulo }}
      </label>
    </li>
    <li v-if="props.tarefasPendentes <= 0" class="list-group-item">Não exite tarefas pendentes</li>
  </ul>
</template>

<style scoped>
.done {
  text-decoration: line-through;
}
</style>
