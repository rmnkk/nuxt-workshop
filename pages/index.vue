<template>
  <div class="container">
    <p>The cute dog below</p>
    <img :src="imgSrc" alt="" />
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
