<template>
  <div class="counter">
      <h4 v-if="filmArray.length <= 0">Non ci sono film disponibili con questo titolo, effettua una nuova ricerca</h4>
      <h4 v-else>Abbiamo Trovato <span>{{filmArray.length}}</span> film</h4>
  </div>
</template>

<script>
export default {
    name: 'Counter',

    props: {
        filmArray: Array,
    }
}
</script>

<style scoped lang="scss">
.counter {
    h4 {
        font-size: 20px;
        font-weight: 300;
        span {
            font-weight: 900;
            color: red;
        }
    }
}



</style>