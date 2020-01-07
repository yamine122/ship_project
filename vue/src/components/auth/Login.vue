<template>
<div id="app">
  <v-btn color="blue" dark fixed center @click="dialog = !dialog"> login </v-btn>
    <v-dialog v-model="dialog" width="400px">
      <v-card>
        <v-card-title class="blue darken-2" font-color="white"> LOGIN </v-card-title>
        
        <v-container fluid >
          <v-layout wrap >
            <v-flex xs8  >
              <v-text-field center prepend-icon="people" v-model="userid" placeholder="ID"></v-text-field>
              <v-text-field prepend-icon="lock" placeholder="PASSWORD" v-model="passwd"></v-text-field>
            </v-flex>
            
          </v-layout>
        </v-container>

      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn text color="primary" @click="login()">LOGIN</v-btn>
        <v-btn text color="red" @click="dialog = false">CANCEL</v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</div>

</template>
<script>
import axios from 'axios'
import {store} from '../../store'
export default {
   data(){
      return {
        context : 'http://localhost:8080',
        result : '',
        userid : '',
        passwd : '',
        person : '',
        state : store.state,
        dialog: false,
      }
   },
   methods:{
        join(){
            this.dialog = false
            this.$router.push({path:'/join'})
        },
      login(){
      let   url = `${this.context}/login`
        let data =  {
         userid : this.userid,
         passwd : this.passwd
        }
        let headers= {
              'authorization': 'JWT fefege..',
              'Accept' : 'application/json',
              'Content-Type': 'application/json'
        }
      axios
      .post(url, data, headers)
      .then(res=>{
            if(res.data.result === "SUCCESS"){
                store.state.person = res.data.person
                if(this.state.person.role != 'student'){
                    // this.state.authCheck = true
                    this.$router.push({path:'/'})
                }else{
                    this.state.authCheck = false
                }
                this.dialog=false
                this.$router.push({path:'/mypage'})
            }else{
                alert(`로그인 실패`)
                this.$router.go({path: '/login'})
            }
         this.result = res.data
      })
      .catch(()=>{
         alert('axios fail')
        })
      }
   }
}
</script>
<style scoped>
.layout {
  justify-content:center;
}
</style>