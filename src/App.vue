<script setup>
const carrinho = [];
const ListaCompras = [
  {
    id: 1,
    nome: 'Camiseta',
    preco: 49.90
  },
  {
    id: 2,
    nome: 'Calça',
    preco: 99.90
  },
  {
    id: 3,
    nome: 'Meia',
    preco: 9.90
  },
  {
    id: 4,
    nome: 'Sapato',
    preco: 199.90
  },
  {
    id: 5,
    nome: 'Boné',
    preco: 29.90
  },
  {
    id: 6,
    nome: 'Óculos',
    preco: 99.90
  },
  {
    id: 7,
    nome: 'Relógio',
    preco: 299.90
  },
  {
    id: 8,
    nome: 'Bermuda',
    preco: 79.90
  },
  {
    id: 9,
    nome: 'Cueca',
    preco: 19.90
  },
  {
    id: 10,
    nome: 'Meia',
    preco: 9.90
  }
]

function somar(index) {
  ListaCompras.value[index].quantidade++
}
function diminuir(index) {
  ListaCompras.value[index].quantidade--
}
function adicionar(index){
  carrinho.push(item)
}
</script>
<template>
  <button>Adicionar No Carrinho</button>
  <div class="itens">
    <ul>
      <li class="lista" v-for="item in ListaCompras" :key="item.id">
        Item: {{ item.nome }} <br>
        Código item: {{ item.id }} <br>
        Preço R${{ item.preco.toFixed(2) }} <br>
        <button @click="somar(index)">+</button>
        <button @click="diminuir(index)">-</button>
        <br>
        <button @click="adicionar">Adicionar</button>
        <br>
      </li>
    </ul>
  </div>
  {{ carrinho }}
</template>

<style scoped>
</style>
