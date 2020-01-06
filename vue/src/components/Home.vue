<template>
<div id="app">
<layout>
   <template #header="h" >
    <v-app id="inspire" >
  <!-- --------------------------------------- 네비 ------------------------------------------ -->
      <div>
        <v-toolbar color="#BDBDBD">
        <v-icon style="margin-left:230px" large color="blue darken-2">mdi-anchor</v-icon>
        <v-toolbar-title @click="home()"> Ship </v-toolbar-title>
        <v-spacer></v-spacer>
          <v-toolbar-items style="margin-right:220px">
            <v-btn text @click="join()">JOIN</v-btn>
            <v-btn text @click="login()">LOGIN</v-btn>
            <v-btn text @click="logout()">LOGOUT</v-btn>
            <v-btn text @click="lol()">LOL</v-btn>
            <v-btn text @click="futsal()">FUTSAL</v-btn>
          </v-toolbar-items>
  
        <!-- <template v-if="$vuetify.breakpoint.smAndUp" >
          <v-btn icon>
            <v-icon >mdi-export-variant</v-icon>
          </v-btn>
          <v-btn icon>
            <v-icon>mdi-delete-circle</v-icon>
          </v-btn>
          <v-btn icon>
            <v-icon >mdi-plus-circle</v-icon>
          </v-btn>
        </template> -->
        </v-toolbar>
      </div>
    </v-app>
  </template>
   <!-- --------------------- 사이드 바  ------------------------- -->
<template #content ="c">
  <div id="app" style="width:1400px" >
    <v-app id="inspire">
        <v-card height="100%">
          <v-navigation-drawer absolute temperate left width="20%">
      <template v-slot:prepend>
              <v-list-item two-line>
              <v-list-item-avatar>
              <img src="https://randomuser.me/api/portraits/women/81.jpg">
            </v-list-item-avatar>
            <v-list-item-content>
              <v-list-item-title>{{state.person.name}}님 환영합니다.</v-list-item-title>
              <v-list-item-subtitle></v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
      </template>
        <v-divider></v-divider>
          <v-list dense>
            <v-list-item v-for="side of sides" :key="side.title" @click="sidego(side.title)">
                <v-list-item-icon>
                  <v-icon>{{ side.icon }}</v-icon>
                </v-list-item-icon>
              <v-list-item-content>
                <v-list-item-title>{{ side.title }}</v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </v-navigation-drawer>
      <!-- ----------------------------------------컨텐츠------------------------------------------ -->
        <v-navigation-drawer absolute right width="80%" >
          <template>
            <router-view></router-view>
          </template>
        </v-navigation-drawer>
      </v-card>
    </v-app>
  </div>
</template>
<template #footer ="f">
  <h1>{{f.title}} </h1>
</template>
</layout>
</div>
</template>

<script>
// import mdiAccount from '@mdi/js'
import Layout from '@/components/cmm/Layout.vue'
import {store} from '@/store'
export default {
  components:{
    Layout
  },
  data(){
   return{
    //  icons: {mdiAccount},
      sides: [
          { title: 'Home', icon: 'mdi-home' },
          { title: 'My Account', icon: 'mdi-account' },
          { title: 'Users', icon: 'mdi-account-group-outline' },
          { title: '풋살 관리', icon: 'mdi-account-group-outline' },
          { title: '신고게시판', icon: 'mdi-account-group-outline' },
          { title: '수익 관리', icon: 'mdi-account-group-outline' },
        ],
      state:store.state
      }
  },
  methods:{
    home(){
      this.$router.push({path:'/'})
    },
    login(){
      this.$router.push({path:'/login'})
    },
    logout(){
      this.state.person={}
      this.$router.push({path:'/'})
    },
    join(){
      this.$router.push({path:'/join'})
    },
    mypage(){
      this.$router.push({path:'/mypage'})
    },
    lol(){
      this.$router.push({path:'/lol'})
    },
    futsal(){
      this.$router.push({path:'/futsal'})
    },
    sidego(x){
      alert(`${x}`)
    }
  }
}
</script>
<style scoped>
@import 'https://fonts.googleapis.com/css?family=Montserrat|Open+Sans';
</style>