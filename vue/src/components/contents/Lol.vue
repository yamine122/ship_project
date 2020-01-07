<template>
<div>
   <v-app>
   <v-row>
      <v-card id="d" class="mx-auto" dark>
      <v-img src="data:image/jpeg;base64,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"></v-img>
         <v-card-subtitle dark>
            <v-card-text>쌉캐리가능 정글구함
               <v-card-actions class="mx-auto">
                  <v-btn text color="primary" @click="joinroom()">참여하기</v-btn>
               </v-card-actions>
            </v-card-text>
         </v-card-subtitle>
      </v-card>
      <v-card id="d" class="mx-auto" dark>
      <v-img src=""></v-img>
         <v-card-subtitle>
            <v-card-text>쌉캐리가능 미드구함
               <v-card-actions>
                  <v-btn text color="primary" @click="joinroom()">참여하기</v-btn>
               </v-card-actions>
            </v-card-text>
         </v-card-subtitle>
      </v-card>
      <v-card id="d" class="mx-auto" dark>
      <v-img src=""></v-img>
         <v-card-subtitle>
            <v-card-text>쌉캐리가능 정글구함
               <v-card-actions>
                  <v-btn text color="primary" @click="joinroom()">참여하기</v-btn>
               </v-card-actions>
            </v-card-text>
         </v-card-subtitle>
      </v-card>
      </v-row>
      <v-row>
      <v-card id="d" class="mx-auto" dark>
      <v-img src=""></v-img>
         <v-card-subtitle dark>
            <v-card-text>쌉캐리가능 정글구함
               <v-card-actions class="mx-auto">
                  <v-btn text color="primary" @click="joinroom()">참여하기</v-btn>
               </v-card-actions>
            </v-card-text>
         </v-card-subtitle>
      </v-card>
      <v-card id="d" class="mx-auto" dark>
      <v-img src=""></v-img>
         <v-card-subtitle>
            <v-card-text>쌉캐리가능 정글구함
               <v-card-actions>
                  <v-btn text color="primary" @click="joinroom()">참여하기</v-btn>
               </v-card-actions>
            </v-card-text>
         </v-card-subtitle>
      </v-card>
      <v-card id="d" class="mx-auto" dark>
      <v-img src=""></v-img>
         <v-card-subtitle>
            <v-card-text>쌉캐리가능 정글구함
               <v-card-actions>
                  <v-btn text color="primary" @click="joinroom()">참여하기</v-btn>
               </v-card-actions>
            </v-card-text>
         </v-card-subtitle>
      </v-card>
      </v-row>
   </v-app>
</div>
</template>
<script>
export default{
   data(){
      return{

      }
   },
   methods:{
      joinroom(){
         this.$router.push({path:'/joinRoom'})
      }
   }
}
</script>
<style scoped>
#d{
   height: 50%
}
</style>