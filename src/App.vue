<template>
  <div id="app">
    <Header @searchFilm="userFilm"/>
    <Main :filmArray="filmList" :seriesArray="seriesList" v-if="this.filmList.length !== 0 || this.seriesList !== 0"/>
    <Loader v-else/>
  </div>
</template>

<script>
import axios from 'axios'
import Header from '@/components/Header.vue'
import Main from '@/components/Main.vue'
import Loader from '@/components/Loader.vue'



export default {
  name: 'App',
  components: {
    Header,
    Main,
    Loader


  },

     created() {
        this.userFilm();
    },

    data() {
        return {
            filmList: [],
            seriesList: [],

            searchedFilm: '',

        }
    },

    methods: {

        userFilm(dato) {
            if (dato === undefined || dato === '') {
                dato = 'a'
            }

            //Films
            axios.get('https://api.themoviedb.org/3/search/movie?', {
                params: {
                    api_key: '519ddeb4aedf4b3d733b4d9c3a5aabe3',
                    query: `${dato.toLowerCase()}`,
                    language: 'it-IT',
                }
            })
            .then(result => {
                this.filmList = result.data.results
            })
            .catch(err => {console.log(err);})

            //Series
            axios.get('https://api.themoviedb.org/3/search/tv?', {
                params: {
                    api_key: '519ddeb4aedf4b3d733b4d9c3a5aabe3',
                    query: `${dato.toLowerCase()}`, 
                    language: 'it-IT',
                }
            })
            .then(result => {
                this.seriesList = result.data.results
            })
            .catch(err => {console.log(err);});
            
            }
    }



}
</script>

<style lang="scss">
@import '@/styles/global.scss'

</style>
