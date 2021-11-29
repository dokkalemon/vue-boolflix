<template>
  <main>

      <Card />

  </main>
</template>

<script>
import Card from '@/components/Card.vue'

export default {
    name: 'Main',
    components: {
        Card
    }
}
</script>

<style scoped lang="scss">
main {
    width: 100%;
}

</style>