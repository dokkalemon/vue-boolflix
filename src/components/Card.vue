<template>
  <ul>
      <li>{{ title }}</li>
      <li v-show="title !== originalTitle">{{ originalTitle }}</li>
      <li v-if="language !== 'en' && language !== 'it'">{{ language }}</li>
      <li v-else><img :src="`${img}`" alt=""></li>
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

    created() {
        this.selectFlag()
    },

    data() {
        return {
            img: '',
        }
    },

    methods: {
        selectFlag() {
            if (this.language === 'it') {
                this.img = require('../assets/it.png')
            } else if (this.language === 'en') {
                this.img = require('../assets/en.png')
  
            }
        }
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