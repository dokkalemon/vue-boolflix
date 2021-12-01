<template>
  <main>

      <Jumbo/>

      <div class="cards">
      <Card 
        v-for="film in filmArray"
        :key="`${film.id}`"
        :id="film.id"
        :title="film.title"
        :originalTitle="film.original_title"
        :language="film.original_language"
        :vote="film.vote_average"
        :image="`https://image.tmdb.org/t/p/w154/${film.poster_path}`"
      />

      <Card 
        v-for="serie in seriesArray"
        :key="`${serie.id}`"
        :id="serie.id"
        :title="serie.name"
        :originalTitle="serie.original_name"
        :language="serie.original_language"
        :vote="serie.vote_average"
        :image="`https://image.tmdb.org/t/p/w154/${serie.poster_path}`"
      />
      </div>
  </main>
</template>

<script>
import Jumbo from '@/components/Jumbo.vue'
import Card from '@/components/Card.vue'

export default {
    name: 'Main',
    components: {
        Card,
        Jumbo
    },

    props: {
        filmArray: Array,
        seriesArray: Array,
    }
}
</script>

<style scoped lang="scss">
main {
    .cards {
      display: flex;
    }
}

</style>