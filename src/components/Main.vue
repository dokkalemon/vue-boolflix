<template>
  <main>

      <Jumbo/>

      <div class="cards px-40">
      <Card 
        v-for="film in filmArray"
        :key="`${film.id}`"
        :id="film.id"
        :title="film.title"
        :originalTitle="film.original_title"
        :language="film.original_language"
        :vote="film.vote_average"
        :image="`https://image.tmdb.org/t/p/original${film.poster_path}`"
        :overwiew="film.overview"
      class="card"/>

      <Card 
        v-for="serie in seriesArray"
        :key="`${serie.id}`"
        :id="serie.id"
        :title="serie.name"
        :originalTitle="serie.original_name"
        :language="serie.original_language"
        :vote="serie.vote_average"
        :image="`https://image.tmdb.org/t/p/original${serie.poster_path}`"
        :overwiew="serie.overview"
      class="card"/>
      </div>
  </main>
  <!-- https://image.tmdb.org/t/p/original/8s4h9friP6Ci3adRGahHARVd76E.jpg -->
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
      flex-wrap: wrap;
      padding-top: 20px;
      margin-bottom: 150px;
    }

    .card {
      left: 0;
      right: 0;
      transition: all 0.4s ease;
      position: relative;
      &:nth-child(5n+1):hover {

        left: 110px;
      }
      &:nth-child(5n+5):hover {
        left: -110px;
      }
    }
}

</style>