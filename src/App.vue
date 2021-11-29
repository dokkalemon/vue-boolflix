<template>
  <div id="app">
    <Header />
    <Main :filmArray="filmList"/>
  </div>
</template>

<script>
import axios from 'axios'
import Header from '@/components/Header.vue'
import Main from '@/components/Main.vue'

export default {
  name: 'App',
  components: {
    Header,
    Main

  },

     created() {
        this.getFilm()
    },

    data() {
        return {
            filmList: null,
        }
    },

    methods: {

        getFilm() {
            
            axios.get('https://api.themoviedb.org/3/search/movie?', {
                params: {
                    api_key: '519ddeb4aedf4b3d733b4d9c3a5aabe3',
                    query: 'ritorno al futuro'
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
