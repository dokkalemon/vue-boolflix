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

    props: {
        title: String,
        originalTitle: String,
        language: String,
        vote: String
    }


}
</script>

<style>

</style>