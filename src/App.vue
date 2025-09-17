<script lang="ts">
export default {
  data() {
    return {
      perguntas: [{ nome: "Estudar vue.js", concluida: false },
      { nome: "Ler documentação do Vue 3", concluida: false },
      { nome: "Praticar v-if e v-for", concluida: false }
      ]
    }
  },
  methods: {
    checkboxAtivoOuNao(index: number) {
      this.perguntas[index].concluida = !this.perguntas[index].concluida
    }
  },
  computed: {
     todasConcluidas() {
      return this.perguntas.every(item => item.concluida)
     }
  }
}
</script>

<template>
  <ul class="corpo__perguntas">
    <li v-for="(item,index) in perguntas" :key="index">
      {{ item.nome }}
      <input type="checkbox" v-model="item.concluida"/> 
      <div v-if="todasConcluidas === true">
        <p>Parabéns! Você concluiu todas as tarefas!</p>
        </div>
       
      

    </li>
  </ul>
 

</template>

<style scoped>
.corpo__perguntas {
  list-style: none; /* Remove as bolinhas padrão do li */
  padding: 0;
  max-width: 500px;
  margin: 2rem auto; /* Centraliza na tela */
  font-family: Arial, sans-serif;
}

.corpo__perguntas li {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: #f9f9f9;
  padding: 1rem;
  margin-bottom: 1rem;
  border-radius: 8px;
  box-shadow: 0 2px 6px rgba(0,0,0,0.1);
}

.corpo__perguntas input[type="checkbox"] {
  width: 20px;
  height: 20px;
  cursor: pointer;
}

.corpo__perguntas p {
  margin: 0;
  color: #2c3e50;
  font-weight: bold;
}

.corpo__perguntas li input:checked + p {
  text-decoration: line-through;
  color: #7f8c8d;
}

div[v-cloak] {
  display: none;
}

div p {
  text-align: center;
  color: #27ae60;
  font-weight: bold;
  margin-top: 1rem;
  font-size: 1.1rem;
}
</style>
