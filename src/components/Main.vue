<template>
  <main>

      <Jumbo/>
      <!-- Card conteiner -->
      <div class="cards px-40">
      <Card 
        v-for="film in filmArray"
        :key="`${film.id}`"
        :id="film.id"
        :title="film.title"
        :originalTitle="film.original_title"
        :language="film.original_language"
        :vote="film.vote_average"
        :image="`https://image.tmdb.org/t/p/w342${film.poster_path}`"
        :overwiew="film.overview"
        @getId="getInfoFilm"
      class="card"/>

      <Card 
        v-for="serie in seriesArray"
        :key="`${serie.id}`"
        :id="serie.id"
        :title="serie.name"
        :originalTitle="serie.original_name"
        :language="serie.original_language"
        :vote="serie.vote_average"
        :image="`https://image.tmdb.org/t/p/w342${serie.poster_path}`"
        :overwiew="serie.overview"
        @getId="getInfoSerie"
      class="card"/>
      </div>

    <div class="philter" :class="{active: activeInfo}" @click="hiddenInfo()"></div>
    <Info :activeInfo="activeInfo" class="info" :infoFilm="infoFilm" :nameActor="actorFilm" :relatedFilm="relatedFilm"/>


  </main>
</template>



<script>
import axios from 'axios'
import Jumbo from '@/components/Jumbo.vue'
import Card from '@/components/Card.vue'
import Info from '@/components/Info.vue'



export default {
    name: 'Main',
    components: {
        Card,
        Jumbo,
        Info,

    },

    props: {
        filmArray: Array,
        seriesArray: Array,
    },

    data() {
      return {
        activeInfo: false,
        infoFilm: {},
        actorFilm: [],
        relatedFilm: [],
        genreFilm: []
      }
    },

    methods: {

      /* Card:hover show the info */
      hiddenInfo() {
        this.activeInfo = false;
      },


        /* API for Films */
        getInfoFilm(dato) {
            //getfilm
            this.activeInfo = true;

            axios.get(`https://api.themoviedb.org/3/movie/${dato}`, {
              params: {
                api_key: '519ddeb4aedf4b3d733b4d9c3a5aabe3',
                language: 'it-IT'
              }
            })
            .then(result => {
              this.infoFilm = result.data;
            })
            .catch(err => {console.log(err);})
            
            
            //getFilmCast
            axios.get(`https://api.themoviedb.org/3/movie/${dato}/credits`, {
              params: {
                api_key: '519ddeb4aedf4b3d733b4d9c3a5aabe3',
                language: 'it-IT'
              }
            })
            .then(result => {
              this.actorFilm = result.data.cast;
            })
            .catch(err => {console.log(err);})

            //related film
            axios.get(`https://api.themoviedb.org/3/movie/${dato}/similar`, {
              params: {
                api_key: '519ddeb4aedf4b3d733b4d9c3a5aabe3',
                language: 'it-IT'
              }
            })
            .then(result => {
              this.relatedFilm = result.data.results;
            })
            .catch(err => {console.log(err)})



      },

      
      /* API for Series */ 
      getInfoSerie(dato) {
        console.log(dato);

        //serie
        this.activeInfo = true;

        axios.get(`https://api.themoviedb.org/3/tv/${dato}`, {
          params: {
            api_key: '519ddeb4aedf4b3d733b4d9c3a5aabe3',
            language: 'it-IT'
          }
        })
        .then(result => {
          this.infoFilm = result.data;
        })
        .catch(err => {console.log(err);})

        //getCast
        axios.get(`https://api.themoviedb.org/3/tv/${dato}/credits`, {
          params: {
            api_key: '519ddeb4aedf4b3d733b4d9c3a5aabe3',
            language: 'it-IT'
          }
        })
        .then(result => {
          this.actorFilm = result.data.cast;
        })
        .catch(err => {console.log(err);})

        //related serie
        axios.get(`https://api.themoviedb.org/3/tv/${dato}/similar`, {
          params: {
            api_key: '519ddeb4aedf4b3d733b4d9c3a5aabe3',
            language: 'it-IT'
          }
        })
        .then(result => {
          this.relatedFilm = result.data.results;
        })
        .catch(err => {console.log(err)})
      },
    }
}
</script>

<style scoped lang="scss">
@import '@/styles/vars.scss';
main {
  h2 {
    color: $text;
    padding: 20px 40px 0 40px;
    font-weight: 300;
  }

    .cards {
      display: flex;
      flex-wrap: wrap;
      padding-top: px;
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

    .info {
      z-index: 888;
    }
    .philter {
      position: fixed;
      height: 100vh;
      width: 100%;
      background-color: rgba(0, 0, 0, 0.851);
      top:0;
      z-index: 80;
      display: none;
    }

    .active {
      display: block;
    }
}

</style>