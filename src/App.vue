<script setup>

import { ref } from 'vue'


const listaCompras = ref([
  { 
    id: 1,
    nome: 'Champion Sports Bola de basquete de nylon resistente oficial',
    preco: 107.60,
    quantidade: 0,
  },
  {
    id: 2,
    nome: 'Calça',
    preco: 99.90,
    quantidade: 0,
  },
  {
    id: 3,
    nome: 'Meia',
    preco: 9.90,
    quantidade: 0,
  },
  {
    id: 4,
    nome: 'Sapato',
    preco: 199.90,
    quantidade: 0,
  },
  {
    id: 5,
    nome: 'Boné',
    preco: 29.90,
    quantidade: 0,
  },
  {
    id: 6,
    nome: 'Óculos',
    preco: 99.90,
    quantidade: 0,
  },
  {
    id: 7,
    nome: 'Relógio',
    preco: 299.90,
    quantidade: 0,
  },
  {
    id: 8,
    nome: 'Bermuda',
    preco: 79.90,
    quantidade: 0,
  },
  {
    id: 9,
    nome: 'Cueca',
    preco: 19.90,
    quantidade: 0,
  },
  {
    id: 10,
    nome: 'Meia',
    preco: 9.90,
    quantidade: 0,
  }
])
const carrinhos = ref({
  items: [],
  total: 0,

})
function incrementar(index) {
  listaCompras.value[index].quantidade++
}
function decrementar(index) {
  if (listaCompras.value[index].quantidade > 0) {
    listaCompras.value[index].quantidade--
  }
}
function adicionar(index) {
  if (listaCompras.value[index].quantidade > 0) {

    carrinhos.value.items.push(
      { ...listaCompras.value[index], preco: listaCompras.value[index].quantidade * listaCompras.value[index].preco }
    );
    carrinhos.value.total = carrinhos.value.total + listaCompras.value[index].preco * listaCompras.value[index].quantidade
  }
}
function carrinho(index) {

}
</script>

<template>
  <div class="titulo">
    <h1>Bolas.com</h1>
  </div>

  <div class="produtos">
    <div class="lista" v-for="(item, index) in listaCompras" :key="item.id">
      <p> {{ item.nome }} <br>
        Preco: {{ item.preco }} <br>
        ID: {{ item.id }} <br>
        quantidade: {{ item.quantidade }} <br>
        <button @click="incrementar(index)">+</button>
        <button @click="decrementar(index)">-</button>
        <button @click="adicionar(index)">Adicionar</button>
      </p>
    </div>
  
  </div>
  <hr>

  <div class="carrinho">

    <div class="" v-for="item in carrinhos.items">
      <p>Item: {{ item.nome }} <br>
        Preco: {{ item.preco.toFixed(2) }} <br>
        ID: {{ item.id }} <br>
        Quantidade: {{ item.quantidade }} <br>
        <button @click="RemoverCarrinho">Remover</button>
      </p>

    </div>
    <p> Total:{{ carrinhos.total.toFixed(2) }}</p>
  </div>
</template>

<style scoped>
.titulo {
  text-align: center;
  padding-bottom: 40px;
}
.produtos{
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: 200px;
  text-align: center;

}
.carrinho {}
</style>