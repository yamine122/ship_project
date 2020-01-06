<template>
<div id="app">
  <v-app id="inspire">
    <v-content>
      <v-container fluid>
        <v-layout justify-center>
          <v-flex md5>
            <v-card class="elevation-12">
              <v-toolbar color="primary" dark flat>
                <v-toolbar-title>Login form</v-toolbar-title>
                <v-spacer></v-spacer>
                <v-tooltip bottom>
                </v-tooltip>
                <v-tooltip right>
                  <template v-slot:activator="{ on }">
                    <v-btn
                      icon
                      large
                      href="https://codepen.io/johnjleider/pen/pMvGQO"
                      target="_blank"
                      v-on="on"
                    >
                      <v-icon>mdi-codepen</v-icon>
                    </v-btn>
                  </template>
                  <span>Codepen</span>
                </v-tooltip>
              </v-toolbar>
              <v-card-text>
                <v-form>
                  <v-text-field
                    label="ID"
                    name="id"
                    prepend-icon=""
                    type="text"
                  ></v-text-field>

                  <v-text-field
                    id="password"
                    label="PASSWORD"
                    name="password"
                    prepend-icon=""
                    type="password"
                  ></v-text-field>
                </v-form>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="primary">Login</v-btn>
              </v-card-actions>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>
  </v-app>
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