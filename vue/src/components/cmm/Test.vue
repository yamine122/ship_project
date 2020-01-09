<template>
<div id="app">
    <v-container class="pa-4 text-center">
      <v-row class="fill-height" align="center" justify="center">
        <template v-for="(item, i) in items">
          <v-col
            :key="i"
            cols="12"
            md="4"
          >
            <v-hover v-slot:default="{ hover }">
              <v-card
                :elevation="hover ? 12 : 2"
                :class="{ 'on-hover': hover }"
              >
                <v-img
                  :src="item.img"
                  height="225px"
                >
                  <v-card-title class="title white--text">
                    <v-row
                      class="fill-height flex-column"
                      justify="space-between"
                    >
                      <p class="mt-4 subheading text-left">{{ item.title }}</p>
  
                      <div>
                        <p class="ma-0 body-1 font-weight-bold font-italic text-left">
                          {{ item.text }}
                        </p>
                        <p class="caption font-weight-medium font-italic text-left">
                          {{ item.subtext }}
                        </p>
                      </div>
  
                      <div class="align-self-center">
                        <v-btn
                          v-for="(icon, index) in icons"
                          :key="index"
                          :class="{ 'show-btns': hover }"
                          color="transparent"
                          icon
                        >
                          <v-icon
                            :class="{ 'show-btns': hover }"
                            color="transparent"
                          >
                            {{ icon }}
                          </v-icon>
                        </v-btn>
                      </div>
                    </v-row>
                  </v-card-title>
                </v-img>
              </v-card>
            </v-hover>
          </v-col>
        </template>
      </v-row>
    </v-container>
</div>
</template>

<script>
export default {
  data () {
    return {
      contents: [
        { text: 'LOL' },
        { text: 'FUTSAL' },
      ],
      radios: 'radio-1',
      link:'/mypage',
      date: null,
      trip: {
      name: '',
      location: null,
      start: null,
      end: null,
    }
    }
  },
  methods:{
    radiogo(x){
      this.$router.push({path:`${x}`})
    }
  }
}
</script>

<style scoped>
</style>