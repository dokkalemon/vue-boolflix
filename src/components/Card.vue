<template>
  <ul>
      <li>{{ title }}</li>
      <li v-show="title !== originalTitle">{{ originalTitle }}</li>
      <li>
            <img v-if="isFlag" :src="require(`../assets/${language}.png`)" alt="">
            <span v-else> {{language}} </span>
      </li>
      <li>{{ vote }}</li>
  </ul>
</template>

<script>

export default {
    name: 'Card',

    props: {
        title: String,
        originalTitle: String,
        language: String,
        vote: Number
    },

    computed: {
        isFlag() {
            return this.availableFlag.includes(this.language)
        }
    },

    data() {
        return {
            availableFlag: ['it', 'en'],
        }
    },

    methods: {
        
    }


}
</script>

<style scoped lang="scss">

ul {
    li {
        img {
            height: 15px;
        }
    }
}

</style>