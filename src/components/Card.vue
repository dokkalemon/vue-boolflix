<template>
  <ul>
      <li>Titolo:</li>
      <li>Titolo Originale</li>
      <li>Lingua</li>
      <li>Voto</li>
  </ul>
</template>

<script>
export default {
    name: 'Card',

    created() {
        this.getFilm(r)
    },

    data() {
        return {
            filmList: [],
        }
    },

    methods: {

        getFilm() {
            console.log('cioao');
        }
    }

}
</script>

<style>

</style>