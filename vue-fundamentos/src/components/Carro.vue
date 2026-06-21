<script setup>
    // outra forma de definir as props
    const props = defineProps(['imagem', 'nome', 'ano', 'descricao'])
</script>
<template>
    <div>
        <img 
        :src="props.imagem"
        width="100%"
        height="auto"
        >
        <h2>{{ props.nome }}</h2>
        <p>
            <slot name="estado">Novo</slot>
        </p>
        <p>
            <slot name="cambio">Automático</slot>
        </p>
        <h3>{{ props.ano }}</h3>
        <p>{{ props.descricao }}</p>
    </div>
</template>
<style scoped>
    h2,h3 {
        margin: 0 0 0.5rem;
    }
</style>