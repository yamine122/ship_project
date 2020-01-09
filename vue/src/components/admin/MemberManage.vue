<template>
  <div style="margin:10px;">
  <div class="text-center" style="">
    <v-sheet color="grey" style="font-size:xx-large">회원 목록 관리 <v-btn style= "float:right;color:red; height:48px" @click="blacklist()">블랙리스트 관리</v-btn></v-sheet>
    
  </div>
   <v-card>
    <v-card-title>
      <v-text-field
        v-model="search"
        append-icon="search"
        label="Search"
        single-line
        hide-details
        style="width:300px;"
      ></v-text-field>
    </v-card-title>
    <v-data-table
      :headers="headers"
      :items="lists"
      :search="search"
    >
    <template v-slot:item.male="{ item }" >
      <v-checkbox v-model="item.male" :label="`${item.male}`"></v-checkbox>
    </template>
    </v-data-table>
  </v-card>
  <!-- <v-card>
    <v-simple-table
      :fixed-header="fixedHeader"
    >
      <template v-slot:default class="text-center" >
      
      <thead >
          <tr style="font-size:large">
         <th class="text-left">고유번호</th>
         <th class="text-left">아이디</th>
         <th class="text-left">비밀번호</th>
         <th class="text-left">이름</th>
         <th class="text-left">생일</th>
         <th class="text-left">성별</th>
         <th class="text-left">연락처</th>
         <th class="text-left">이메일</th>
         <th class="text-left">포인트</th>
         <th class="text-left">구분</th>
         <th class="text-left" color="red">블랙 등록</th>
          </tr>
        </thead>

        <tbody>
        <tr v-for="j of lists" :key="j.userid" @click="member(j.name)">
         <td>{{j.personid}}</td>
         <td>{{j.userid}}</td>
         <td>{{j.passwd}}</td>
         <td>{{j.name}}</td>
         <td>{{j.birthday}}</td>
         <td>{{(j.male==1)?'남성':'여성'}}</td>
         <td>{{j.tel}}</td>
         <td>{{j.email}}</td>
         <td>{{j.score}}</td>
         <td>{{j.role}}</td>
         <v-checkbox v-model="`{{(j.black)?}}`" label="black"></v-checkbox>
          </tr>
        </tbody>

      </template>
    </v-simple-table>
   <div class="text-center">
    <v-pagination
    v-model="value"
   value
    :length="5"
   circle
   prev-icon="mdi-arrow-left"
   next-icon="mdi-arrow-right"
    ></v-pagination>
 
  </div>
   </v-card> -->
  </div>
</template>
<script>
// import axios from 'axios'
export default {
  // created(){
  //   axios
   //       .get(`${this.context}/customermanage`)
   //       .then(res =>{
   //          this.lists = res.data
   //       })
   //       .catch(e=>{
   //          alert('AXIOS FAIL'+e)
   //       })
  // },
   data(){
      return{
    context : 'http://localhost:8080',
      fixedHeader: true,
      value:1,
    lists: [],
    black:false,
    search: '',
        headers: [
          {
            text: '회원 리스트 ',
            align: 'left',
            filterable: true,
            value: 'name',
          },
          { text: '고유번호', value: 'personid' },
          { text: '아이디', value: 'userid' },
          { text: '비밀번호', value: 'passwd' },
          { text: '이름', value: 'name' },
          { text: '생일', value: 'birthday' },
          { text: '연락처', value: 'tel' },
          { text: '이메일', value: 'email' },
          { text: '포인트', value: 'score' },
          { text: '구분', value: 'role' },
          { text: '블랙 등록', value: 'male'},
        ],
      }
   },
   methods:{
    blacklist(){
      alert('블랙 리스트 관리 창으로 이동  ')
    },
    member(x){
      alert(x+'님 개인 설정')
    }

   }
  }
</script>
<style scoped></style>