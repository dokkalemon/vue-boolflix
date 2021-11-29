<template>
  <div id="app">
    <Header @searchFilm="userFilm"/>

    <Main :filmArray="filmList" v-if="filmList !== null"/>

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
        this.getFilm()
    },

    data() {
        return {
            filmList: null,

            searchedFilm: '',

        }
    },

    methods: {

        getFilm() {
            
            axios.get('https://api.themoviedb.org/3/search/movie?', {
                params: {
                    api_key: '519ddeb4aedf4b3d733b4d9c3a5aabe3',
                    query: 'a',
                    language: 'it-IT'
                }
            })
            .then(result => {
                this.filmList = result.data.results
            })

            },

            userFilm(dato) {
              axios.get('https://api.themoviedb.org/3/search/movie?', {
                params: {
                    api_key: '519ddeb4aedf4b3d733b4d9c3a5aabe3',
                    query: `${dato.toLowerCase()}`
                }
            })
            .then(result => {
                this.filmList = result.data.results
            })

            
            }
    }



}
</script>

<style lang="scss">

</style>
