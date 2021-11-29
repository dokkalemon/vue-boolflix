<template>
  <main>

      <Card />

  </main>
</template>

<script>
import axios from 'axios'
import Card from '@/components/Card.vue'

export default {
    name: 'Main',
    components: {
        Card
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

<style scoped lang="scss">
main {
    width: 100%;
}

</style>