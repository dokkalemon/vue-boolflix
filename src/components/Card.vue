<template>
  <ul>
      <li>{{ title }}</li>
      <li v-show="title !== originalTitle">{{ originalTitle }}</li>
      <li>
            <img v-if="isFlag" :src="require(`../assets/${language}.png`)" alt="">
            <span v-else> {{language}} </span>
      </li>
      <li>{{ Math.round(vote / 2) }}</li>
      <li>
          <div class="poster">
              <img :src="image" alt="">
          </div>
      </li>
  </ul>
</template>

<script>

export default {
    name: 'Card',

    props: {
        title: String,
        originalTitle: String,
        language: String,
        vote: Number,
        image: String
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
        .poster {
            img {
            height: auto
        }
        }
        
    }
}

</style>