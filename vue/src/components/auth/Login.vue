<template>

  <v-row justify="center">
    <v-dialog v-model="dialog" width="500" height="1000" >
      <template v-slot:activator="{on}">
        <v-btn color="primary" dark v-on="on">로그인</v-btn>
      </template>
      <v-card >
        <v-card-title class="headline">로그인</v-card-title>
        <v-card-text>ship homepage에 오신 것을 환영합니다</v-card-text>
        <v-text-field  style="width:200px;" label="ID를 입력해주세요 "  hide-details="auto" v-model="userid"></v-text-field>
        <v-text-field label="PW를 입력해주세요" v-model="passwd"></v-text-field>
        <v-card-actions >
          <v-spacer></v-spacer>
          <v-btn color="green" text @click="login()">LOGIN</v-btn>
          <v-btn color="warning" text @click="dialog= false">cancel</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>

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
</style>