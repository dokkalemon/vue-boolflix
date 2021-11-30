<template>
    <form action="">
        <input type="text" placeholder="Inserisci il titolo di un film" v-model.trim="userSearch">
        <button type="submit" @click.prevent="$emit('searchFilm', userSearch)">Search</button>
    </form>
</template>

<script>
export default {
    name: 'Header',

    data() {
        return {
            userSearch: '',
        }
    }
}
</script>

<style scoped lang="scss">

</style>