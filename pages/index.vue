<template>
  <div class="container">
    <span>The cute dog below</span>
    <img :src="imgSrc" alt="" />

    <button @click="getRandomDogImage">Get a picture of random dog</button>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  async asyncData({ $axios }) {
    const response = await $axios.get('https://dog.ceo/api/breeds/image/random')
    const imgSrc = response.data.message

    return { imgSrc }
  },
  data() {
    return {
      imgSrc: '',
    }
  },
  methods: {
    async getRandomDogImage() {
      const response = await this.$axios.get(
        'https://dog.ceo/api/breeds/image/random'
      )
      const result = response.data.message

      this.imgSrc = result
    },
  },
}
</script>

<style>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
