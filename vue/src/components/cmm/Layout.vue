<template>
<div id="wrapper">
     <header id="header">
   <slot name="header" :title="header"></slot>
   </header>
   <aside id="sidebar">
   <slot name="sidebar"></slot>
   </aside>
   <section id="content">
   <slot name="content" :content="content"></slot>
   </section>
   <footer id="footer">
   <div class="container">
   <v-footer style="justify-content:center">
     <div v-for="f of footer" :key="f.text"  >
     <h3 style="margin-right:50px">{{f.text}}</h3>
     <a>{{f.title}}</a>
     
     </div>
   </v-footer>
      </div>
   </footer>
</div>
</template>
<script>
export default {
     data(){
          return{
               footer:[
                    {text:'매치', title:'전체 매치'},
                    {text:'서비스 지역 ', title:'서울'},
                    {text:'소셜 미디어', title:'인스타그램'}
               ]
          }
     }
}
</script>
<style scoped>
#wrapper {
     text-align: -webkit-center;
     min-width:1200px;
}
header {
     height: 66px;
}
#content {
     /* margin: 0 auto; */
     /* width: 1400px; */
     /* float: left; */
     /* padding: 5px 15px; */
}
/* #sidebar {
     margin: 50px 0px 0px 0px;
     width: 350px;
     padding: 5px 15px;
     float: left; 
} */
footer {
     /* clear: both; */
}
/* 가로폭 980보다 작을 때 사용할 @media query */
@media screen and (max-width: 980px) {     
     #pagewrap {
           width: 94%;
     }
     #content {
           clear: both;
           padding: 1% 4%;
           width: auto;
           float: none;
     }
     #sidebar {
           clear: both;
           padding: 1% 4%;
           width: 300px;
           float: none;
     }
     header, footer {
           padding: 1% 4%;
     }
}
</style>