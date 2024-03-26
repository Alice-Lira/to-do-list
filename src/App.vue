<script setup>
import { ref } from 'vue';

const tarefas = ref([]);

const tarefa = ref('');

const errorTarefa = ref("");

function adcionar() {

  errorTarefa.value = ''

  if (tarefa.value == null || tarefa.value == '') {
    errorTarefa.value = 'campo obrigatório'
    return
  }

  tarefas.value.push(tarefa.value)
  tarefa.value = ''

}

function excluir(indice) {
  tarefas.value.splice(indice, 1)

}
</script>

<template>
  <div class="container">

    <div class="fundo">
      <h1 class="titulo">To-Do List</h1>

      <div class="div-tarefa">
        <input v-model="tarefa" type="text" name="tarefa" placeholder=" Digite uma tarefa" />
        <button @click="adcionar" type="submit" class="botao">Adicionar</button>
      </div>

      <p v-if="errorTarefa" class="mensagemErro">{{ errorTarefa }}</p>

      <div class="div-checkbox">
        <div v-for="(item, indice) in tarefas" class="tarefa">
          <div>
            <input type="checkbox" class="campo-checkbox" />
            <label class="texto-checkbox" for="campo-checkbox">{{ item }}</label>
          </div>
          <input @click="excluir(indice)" type="image" src="https://cdn-icons-png.flaticon.com/512/10728/10728089.png"
            alt="imagem excluir" class="imagem-excluir" />
        </div>
      </div>

    </div>
  </div>
</template>

<style scoped>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: Arial, Helvetica, sans-serif;
}

.container {
  flex-direction: column;
  align-items: center;
  height: 100vh;
  display: flex;
  justify-content: center;
  background-color: #201357;
}

.fundo {
  background-color: white;
  border-radius: 10px;
  padding: 15px;
  width: 25%;
}

.titulo {
  text-align: left;
  color: #201357;
  font-size: 22px;
}

.div-tarefa {
  display: flex;
  justify-content: space-between;
  margin-top: 10px;
}

.div-tarefa input {
  border-radius: 20px;
  border: 0;
  width: 70%;
  outline: none;
  border-color: #ccc;
  background-color: #efebeb;
  padding: 5px;
}

.botao {
  width: 30%;
  border-radius: 20px;
  border: 0;
  padding: 10px;
  font-size: 12px;
  background: #fa5f17;
  color: white;
  cursor: pointer;
}

.imagem-excluir {
  height: 12px;
}

.div-checkbox {
  margin-top: 15px;
}

.tarefa {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 3px;
}

.texto-checkbox {
  margin-left: 6px;
  font-size: 14px;
}

.input-checkbox {
  border-radius: 4px;
  cursor: pointer;
}

.mensagemErro {
  font-size: 14px;
  color: #ff0000;
  margin-top: 4px;
}
</style>
 