<script setup>
    const props = defineProps({
        produto: {
            type: Object,
            required: true,
        }
    })

    const emit = defineEmits(['deletar']);
</script>

<template>
    <div class="product-card">
        <img 
            :src="produto.imagem" 
            :alt="produto.descricao" 
            width="100%" 
            height="180px"
        >
        <h3>{{ produto.nome }}</h3>
        <p>{{ produto.descricao }}</p>
        <span>R$ {{ produto.preco }}</span>
        <button @click="emit('deletar', produto.id)">Deletar</button>
    </div>
</template>

<style scoped>
    .product-card {
        border: 1px solid rgb(197, 197, 197);
        padding: 1rem;
        border-radius: 0.4rem;
        text-align: center;
    }
    .product-card h3,
    .product-card p {
        color: rgb(197, 197, 197);
    }
    .product-card h3 {
        font-weight: 600;
    }
    .product-card span  {
        color: yellow;
    }
</style>