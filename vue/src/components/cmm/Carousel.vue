<template>
<div id="app" style="height:700px">
    <v-carousel cycle height="700px">
      <v-carousel-item v-for="(item,i) in items" :key="i" :src="item.src"
        reverse-transition="fade-transition" transition="fade-transition" @click="carougo(item.link)">
        </v-carousel-item>
    </v-carousel>
</div>
</template>

<script>
export default {
 data () {
    return {
      items: [
        {link:'/futsal',
          src: 'https://www.tff.org/Resources/TFF/FileGallery/4cc681f05905465286110736d23b27c1.jpg'
        },
        {link:'/lol',
          src: 'http://i.imgur.com/bv9OYJ7.jpg',
        },
        {
          src: 'https://cdn.vuetifyjs.com/images/carousel/planet.jpg',
        },
      ],
    }
  },
  methods:{
    carougo(x){
      this.$router.push({path:`${x}`})
    }
  }
}
</script>

<style scoped>
</style>
