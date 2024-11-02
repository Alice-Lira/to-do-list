<script setup>
import { ref } from 'vue';

const tarefas = ref([]);
const tarefa = ref('');
const errorTarefa = ref("");

function adicionar() {

  errorTarefa.value = ''

  if (tarefa.value == null || tarefa.value == '') {
    errorTarefa.value = '*campo obrigatório'
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
  <div className="bg-[#201358] flex items-center justify-center h-[100vh]">
    <div className="bg-white p-5 rounded-lg w-1/2">
      <h1 className="text-left text-[201357] text-xl mb-3">To-Do List</h1>
      <div className="flex justify-between gap-2">
        <input v-model="tarefa" type="text" name="tarefa" placeholder=" Digite uma tarefa"
          className="border-[#201357] border rounded-xl focus:outline-none focus:ring-1 focus:[#201357] w-full p-1" />
        <button @click="adicionar" type="submit"
          className="bg-[#fa5f17] rounded-xl text-white p-2 text-sm w-1/3 hover:bg-orange-400">
          Adicionar
        </button>
      </div>
      <p v-if="errorTarefa" className="text-red-500 text-sm mt-1">{{ errorTarefa }}</p>

      <div className="flex justify-between mt-4">
        <div v-for="(item, indice) in tarefas" className="flex gap-1">
          <input type="checkbox" />
          <label className="text-base" for="campo-checkbox">{{ item }}</label>
        </div>
        <button @click="excluir(indice)" type="image" alt="imagem excluir">
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
            stroke="currentColor" class="size-4 text-red-600">
            <path stroke-linecap="round" stroke-linejoin="round"
              d="m14.74 9-.346 9m-4.788 0L9.26 9m9.968-3.21c.342.052.682.107 1.022.166m-1.022-.165L18.16 19.673a2.25 2.25 0 0 1-2.244 2.077H8.084a2.25 2.25 0 0 1-2.244-2.077L4.772 5.79m14.456 0a48.108 48.108 0 0 0-3.478-.397m-12 .562c.34-.059.68-.114 1.022-.165m0 0a48.11 48.11 0 0 1 3.478-.397m7.5 0v-.916c0-1.18-.91-2.164-2.09-2.201a51.964 51.964 0 0 0-3.32 0c-1.18.037-2.09 1.022-2.09 2.201v.916m7.5 0a48.667 48.667 0 0 0-7.5 0" />
          </svg>
        </button>
      </div>
    </div>
  </div>
</template>