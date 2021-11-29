<template>
    <section class="loader">
        <h3>LOADING...</h3>
    </section>
</template>

<script>
export default {
    name: 'Loader',
}
</script>

<style scoped lang="scss">

.loader {
    position: fixed;
    height: 100vh;
    width: 100%;
    top: 0;
    background-color: white;
    display: flex;
    justify-content: center;
    align-items: center;

    h3 {
        animation: pulse .5s infinite alternate
    }

    @keyframes pulse {
        from {transform: scale(1)}
        to {transform: scale(1.2)}
    }
}


</style>