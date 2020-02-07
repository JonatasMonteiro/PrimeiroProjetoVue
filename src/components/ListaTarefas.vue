<template>
  <div class="teste">
    <Tarefa
      v-for="tarefa in tarefas"
      :tarefa="tarefa"
      @excluiTarefa="excluiTarefa($event)"
      :key="tarefa.id"
      style="display: inline-block;"
    ></Tarefa>
  </div>
</template>

<script>
import Tarefa from "./Tarefa";
export default {
  props: {
    tarefas: Array
  },
  components: { Tarefa },
  methods: {
    excluiTarefa(tarefa) {
      for (var i = 0; i < this.tarefas.length; i++) {
        if (this.tarefas[i] === tarefa) {
          this.tarefas.splice(i, 1);
        }
      }
    }
  }
};
</script>

<style>
.teste {
  width: 900px;
  height: 500px;
}
</style>
