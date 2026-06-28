<script setup>
  import ProductCard from './components/ProductCard.vue';
  import { ref } from "vue";

  const produtos = ref([
    {
      id: 1,
      nome: "Pizza Calabresa",
      descricao:"Pizza de calabresa, queijo e cebola",
      preco: 29.99,
      imagem: "https://swiftbr.vteximg.com.br/arquivos/ids/213885/618283-pizza-artesanal-calabresa_inn.jpg"
    },
    {
      id:2,
      nome:"Pizza 4 Queijos",
      descricao:"Pizza de mussarela, parmesão, provolone e gorgonzola",
      preco: 34.99,
      imagem: "https://alimentos10.com.br/wp-content/uploads/2023/06/imeretian-khachapuri-cheese-lemon-side-view-1.jpg"
    },
    {
      id: 3,
      nome:"Pizza Marguerita",
      descricao:"Pizza de mussarela, tomate, manjericão e azeite",
      preco: 32.99,
      imagem:"https://rossopizza.com.br/salao/wp-content/uploads/2019/09/istock-181175167.jpg"
    }
  ]);

  const novoProduto = ref({
    nome:'',
    descricao:'',
    preco:0,
    imagem:''
  });

  function adicionarProduto(){

    produtos.value.push({
      id: produtos.value.length + 1,
      ...novoProduto.value, 
    });

    novoProduto.value = {
      nome: '',
      descricao: '',
      preco: 0,
      imagem: '',
    }
  }

  function removerProduto(id) {
      produtos.value = produtos.value.filter(p => p.id !== id)
  }
</script>

<template>
  <main>
    <form 
      @submit.prevent="adicionarProduto"
      >
      <h1>Catálogo de produtos</h1>
      <div>
        <label for="nome">Nome:</label>
        <input v-model="novoProduto.nome" id="nome" type="text" required>
      </div>
      <div>
        <label for="descricao">Descrição:</label>
        <input v-model="novoProduto.descricao" id="descricao" type="text" required>
      </div>
      <div>
        <label for="preco">Preço:</label>
        <input v-model="novoProduto.preco" id="preco" type="number" required>
      </div>
      <div>
        <label for="imagem">Imagem URL:</label>
        <input v-model="novoProduto.imagem" id="imagem" type="text" required>
      </div>
      <div>
        <button type="submit">Adicionar Produto</button>
      </div>
    </form>
  </main>
  <section class="products-list">
    <ProductCard
      v-for="produto in produtos"
      :key="produto.id" 
      :produto="produto"
      @deletar="removerProduto"
    />
  </section>
</template>

<style scoped>
h1,
label {
  color: rgb(197, 197, 197);
}
form {
  margin-top: 1rem;
  margin-bottom: 1.8rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}
form label {
  display: block;
  margin-bottom: 0.2rem;
}
form input {
  box-sizing: border-box;
  padding: 0.5rem;
  width: 100%;
  border-radius: 0.2rem;
}
button {
  padding: 0.7rem 1rem;
  background-color: #007bff;
  border: 1px solid #007bff;
  border-radius: 0.2rem;
  color: #ffff;
  max-width: 200px;
}
.products-list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr ));
  gap: 1rem;
}
</style>
