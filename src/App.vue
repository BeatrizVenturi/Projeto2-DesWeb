<script setup>

import { ref } from 'vue'


const listaCompras = ref([
  {
    imagem: "https://m.media-amazon.com/images/I/81o+Tek84rL._AC_SY300_SX300_.jpg",
    id: 1,
    nome: 'Champion Sports Bola de basquete de nylon resistente oficial',
    preco: 107.60,
    quantidade: 0,
  },
  {
    imagem: "https://m.media-amazon.com/images/I/51qo+LsboJL._AC_SX679_.jpg",
    id: 2,
    nome: 'Bola Beisebol com Miolo de Cortiça e Borracha Tamanho 9" Branca Vollo Sports',
    preco: 99.90,
    quantidade: 0,
  },
  {
    imagem: "https://m.media-amazon.com/images/I/511yiaWEm6L._AC_SX679_.jpg",
    id: 3,
    nome: 'Penalty H2L Ultra Fusion X, Bola Handebol Feminino, Amarelo (Yellow), 0.56 Paquete De 6',
    preco: 9.90,
    quantidade: 0,
  },
  {
    imagem: "https://m.media-amazon.com/images/I/61yN2p0XzkL.__AC_SX300_SY300_QL70_ML2_.jpg",
    id: 4,
    nome: 'Penalty Volei VP 5000 X, Bola De Unissex, Amarelo (Yellow), 67 Cm',
    preco: 199.90,
    quantidade: 0,
  },
  {
    imagem: "https://m.media-amazon.com/images/I/61fe8xuThTL._AC_SX679_.jpg",
    id: 5,
    nome: 'Volei De Praia Fun Xxi PENALTY Verde',
    preco: 29.90,
    quantidade: 0,
  },
  {
    imagem: "https://m.media-amazon.com/images/I/61D3g84VpmL.__AC_SX300_SY300_QL70_ML2_.jpg",
    id: 6,
    nome: 'Bola Penalty Campo Lider Xxi',
    preco: 99.90,
    quantidade: 0,
  },
  {
    imagem: "https://m.media-amazon.com/images/I/51+yb0iGhNL._AC_SX679_.jpg",
    id: 7,
    nome: 'Bola de Pilates 55cm Muvin – Antiestouro – Suporta até 300kg – Com Bomba – Ginástica – Fitness – Pilates – Yoga – Fisioterapia – Flexibilidade – Fortalecimento – Tonificação –– Fácil Limpeza',
    preco: 299.90,
    quantidade: 0,
  },
  {
    imagem: "https://m.media-amazon.com/images/I/61X1Ya6KIIL._AC_SX679_.jpg",
    id: 8,
    nome: 'Wilson Bolas de golfe Staff F.L.I. (pacote com 12) brancas',
    preco: 79.90,
    quantidade: 0,
  },
  {
    imagem: "https://m.media-amazon.com/images/I/71zZjxE+CvL._AC_SX679_.jpg",
    id: 9,
    nome: 'Bola de Tênis Head Master Pack com 6 Tubos',
    preco: 199.90,
    quantidade: 0,
  },
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


function RemoverCarrinho(index) {
  if (carrinhos.value.ite.id.findIndex(item => item.id===carrinhos.value.id ) === carrinhos.value.id ) {
    carrinhos.value.id.splice(item.id ,1)
  }
}


</script>

<template>
  <div class="titulo">
    <h1>Bolas.com</h1>
  </div>

  <div class="produtos">
    <div class="lista" v-for="(item, index) in listaCompras" :key="item.id">
      <p>
        <img :src="item.imagem" alt=""> <br>
        {{ item.nome }} <br>
        Preço: R${{ item.preco.toFixed(2) }} <br>
        ID: {{ item.id }} <br>
        Quantidade: {{ item.quantidade }} <br>
        <button @click="incrementar(index)">+</button>
        <button @click="decrementar(index)">-</button>
        <button @click="adicionar(index)">Adicionar</button>
      </p>
    </div>

  </div>


  <div class="carrinho">
    <div class="" v-for="item in carrinhos.items">
      <p>Item: {{ item.nome }} <br>
        Preco: {{ item.preco.toFixed(2) }} <br>
        ID: {{ item.id }} <br>
        Quantidade: {{ item.quantidade }} <br>

        <button @click="RemoverCarrinho">Remover</button>
      </p>
    </div>

  </div>
  <h1> Total: R${{ carrinhos.total.toFixed(2) }}</h1>
</template>

<style scoped>
img {
  width: 150px;
}

.titulo {
  text-align: center;
  padding-bottom: 30px;
  font-size: x-large;
}

.produtos {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: 300px;
  text-align: center;
  padding-bottom: 20px;
}

.carrinho {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: 150px;
  text-align: center;
  border-style: groove;
}

h1 {
  text-align: center;
  padding-top: 10px;
  padding-bottom: 50px;
}</style>