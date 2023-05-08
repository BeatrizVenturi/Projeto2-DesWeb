<script setup>
import { ref } from 'vue';
const ListaCompras = ref([
  {
    id: 1,
    nome: 'Camiseta',
    preco: 49.90,
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
function somar(index) {
  ListaCompras.value[index].quantidade++
}
function diminuir(index) {
  if (ListaCompras.value[index].quantidade > 0) {
    ListaCompras.value[index].quantidade--
  } else {
    ListaCompras.value[index].quantidade = 0
  }
}
function adicionar(index) {
  carrrinhos.value.item.push(...ListaCompras.value(index))
}
const carrrinhos = ref({
  item : [] ,
  preco : 0,
})

</script>
<template>
  <button>Adicionar No Carrinho</button>
  <div class="itens">
    <ul>
      <li class="lista" v-for="(item, index) in ListaCompras" :key="item.id">
        Item: {{ item.nome }} <br>
        Código item: {{ item.id }} <br>
        Preço R${{ item.preco.toFixed(2) }} <br>
        Quantidade: {{ item.quantidade }}
        <br>
        <button @click="somar(index)">+</button>
        <button @click="diminuir(index)">-</button>
        <br>
        <button @click="adicionar">Adicionar</button>
        <br>
      </li>
    </ul>
  </div>
<hr>

  <div class="carrinho">
    <ul>
      <li >
      </li>
    </ul>
  </div>

</template>

<style scoped></style>
