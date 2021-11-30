<template>
  <main>
      <Card 
        v-for="film in filmArray"
        :key="`${film.id}`"
        :title="film.title"
        :originalTitle="film.original_title"
        :language="film.original_language"
        :vote="film.vote_average"
        :image="`https://image.tmdb.org/t/p/w154/${film.poster_path}`"
      />

      <Card 
        v-for="serie in seriesArray"
        :key="`${serie.id}`"
        :title="serie.name"
        :originalTitle="serie.original_name"
        :language="serie.original_language"
        :vote="serie.vote_average"
        :image="`https://image.tmdb.org/t/p/w154/${serie.poster_path}`"
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
        seriesArray: Array,
    }
}
</script>

<style scoped lang="scss">
main {
    width: 100%;
}

</style>