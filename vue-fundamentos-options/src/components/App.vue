<script> 
// remove o setup
  export default {
    data() {
      return {
        number: 0
      }
    },
    methods: {
      operacao(tipo){
        if(tipo === 'adicao')
          this.number++;
        else if(tipo === 'subtracao'){
          this.number--;
          if(this.number < 0)
            this.number = 0;
        }
      }
    }
  }
</script>

<template>
  <p>{{ number }}</p>
  <button @click="operacao('adicao')">+</button>
  <button @click="operacao('subtracao')">-</button>
</template>

<style scoped></style>