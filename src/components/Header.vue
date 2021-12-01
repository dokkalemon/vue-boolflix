<template>
    <header>

        <input type="text" placeholder="Inserisci il titolo di un film" v-model.trim="userSearch" @keyup.enter="$emit('searchFilm', userSearch)">
        <button @click.prevent="$emit('searchFilm', userSearch)">Search</button>

    </header>

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