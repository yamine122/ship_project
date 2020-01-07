<template>
<div id="app" >
  <v-app id="inspire"  >
    <v-carousel cycle height="700px">
      <v-carousel-item v-for="(item,i) in items" :key="i" :src="item.src"
        reverse-transition="fade-transition" transition="fade-transition" @click="carougo(item.link)">
        </v-carousel-item>
    </v-carousel>
  </v-app>
</div>
</template>

<script>
export default {
 data () {
    return {
      items: [
        {
          src: 'https://www.tff.org/Resources/TFF/FileGallery/4cc681f05905465286110736d23b27c1.jpg', link:'/futsal'
        },
        {link:'/lol',
          src: 'https://cdn.guidingtech.com/imager/media/assets/196282/Best-League-of-Legends-Wallpapers-1_935adec67b324b146ff212ec4c69054f.png?1526290830',
        },
        {
          src: 'https://cdn.vuetifyjs.com/images/carousel/bird.jpg',
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
