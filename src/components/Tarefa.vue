<template>
  <div @click="mudaCor(tarefa)" v-if="tarefa.completo" class="green">
    <del>{{ tarefa.texto }}</del>
    <button
      @click="excluiTarefa(tarefa)"
      style="background:darkgreen"
      class="botaoExcluir"
    >
      x
    </button>
  </div>
  <div @click="mudaCor(tarefa)" v-else class="red">
    {{ tarefa.texto }}
    <button
      @click="excluiTarefa(tarefa)"
      style="background:darkred"
      class="botaoExcluir"
    >
      x
    </button>
  </div>
</template>

<script>
export default {
  props: {
    tarefa: null
  },
  methods: {
    mudaCor(tarefa) {
      tarefa.completo = !tarefa.completo;
    },
    excluiTarefa(tarefa) {
      this.$emit("excluiTarefa", tarefa);
    }
  }
};
</script>

<style>
.red {
  width: 150px;
  height: 120px;
  background: red;
  position: relative;
  border-radius: 15px;
  text-align: center;
  margin-left: 15px;
  word-wrap: break-word;
}
.green {
  width: 150px;
  height: 120px;
  position: relative;
  background: green;
  border-radius: 15px;
  text-align: center;
  margin-left: 15px;
  word-wrap: break-word;
}
.botaoExcluir {
  width: 15px;
  height: 15px;
  position: absolute;
  border-radius: 10px;
  top: 3px;
  right: 5px;
  font-size: 10px;
}
</style>
