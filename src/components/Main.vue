<template>
  <main>

      <Card 
        v-for="film in filmArray"
        :key="`${film.id}`"
        :title="film.title"
        :originalTitle="film.original_title"
        :language="film.original_language"
        :vote="film.vote_average"
      />

  </main>
</template>

<script>
import Card from '@/components/Card.vue'

export default {
    name: 'Main',
    components: {
        Card
    },

    props: {
        filmArray: Array,
    }



}
</script>

<style scoped lang="scss">
main {
    width: 100%;
}

</style>