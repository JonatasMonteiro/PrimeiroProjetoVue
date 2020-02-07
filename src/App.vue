<template>
  <div id="app">
    <h1>Tarefas</h1>
    <Progresso :porcentagem="atualizaProgresso"></Progresso>
    <input style="display: inline-block;" v-model="tarefaTexto" />
    <button
      style="display: inline-block;"
      @click="
        adicionaTarefa({ id: ident, texto: tarefaTexto, completo: false })
      "
    >
      +
    </button>
    <lista-tarefas :tarefas="tarefas" />
  </div>
</template>

<script>
import ListaTarefas from "./components/ListaTarefas";
import Progresso from "./components/Progresso";

export default {
  components: { "lista-tarefas": ListaTarefas, Progresso },
  data() {
    return {
      tarefas: [],
      tarefaTexto: "",
      ident: 0
    };
  },
  methods: {
    adicionaTarefa(tarefa) {
      this.tarefas.push(tarefa);
      this.ident = this.ident + 1;
    }
  },
  computed: {
    atualizaProgresso() {
      let count = 0;
      let flag = true;
      for (var i = 0; i < this.tarefas.length; i++) {
        if (this.tarefas[i].completo) {
          count = count + 1;
          flag = false;
        }
      }
      if (flag) {
        return 0;
      }
      return (count / this.tarefas.length) * 1000;
    }
  }
};
</script>

<style>
body {
  font-family: "Lato", sans-serif;
  background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
  color: #fff;
}

#app {
  display: flex;
  flex: 1;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

#app h1 {
  margin-bottom: 5px;
  font-weight: 300;
  font-size: 3rem;
}
input {
  width: 100px;
  height: 20px;
  border: red;
}
</style>
