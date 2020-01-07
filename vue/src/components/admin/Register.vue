<template>
<v-app>
<v-row style="margin:20px;float:left;">

<div class="card" style="text-align:center;width:700px;">
 
  <div class="card-body">
    <h3 class="card-title">구장 등록</h3>
    <div style="margin:20px;padding:20px">
   

<div>
<form class="form-horizontal" action="" method="post" enctype="multipart/form-data">
<div class="form-group row">
<label class="col-md-3 col-form-label" for="text-input" style="">구장 이름</label>
<div class="col-md-9">
<input class="form-control" id="text-input" type="text" name="text-input" placeholder="신촌 1경기장">
</div>
</div>
<div class="form-group row">
<label class="col-md-3 col-form-label" for="text-input">관리자 이름</label>
<div class="col-md-9">
<input class="form-control" id="text-input" type="text" name="text-input" placeholder="이름">
</div>
</div>
<div class="form-group row">
<label class="col-md-3 col-form-label">관리자 연락처 </label>
<div class="col-md-9">
<input class="form-control" id="tel-input" type="tel" name="tel-input" placeholder="연락처 ">
</div>
</div>
<div class="form-group row">
<label class="col-md-3 col-form-label" for="email-input">관리자  Email </label>
<div class="col-md-9">
<input class="form-control" id="email-input" type="email" name="email-input" placeholder="Email" autocomplete="email">
</div>
</div>
<!-- <div class="form-group row">
<label @click="show()" type="date" class="col-md-3 col-form-label" for="date-input">경기 구장 등록 날짜 입력</label>

<div class="col-md-9">

<input class="form-control" id="date-input" type="date" name="date-input" placeholder="date">
</div>
</div> -->
<div class="form-group row">
<label class="col-md-3 col-form-label" for="disabled-input">경기 예약  비용</label>
<div class="col-md-9">
<input class="form-control" id="disabled-input" type="text" name="disabled-input" placeholder="10000원" disabled="">
</div>
</div>

<div class="form-group row">
<label class="col-md-3 col-form-label" for="select1">경기 인원 선택</label>
<div class="col-md-9">
<select class="form-control" id="select1" name="select1">
<option value="0">- - - - - - - - - -</option>
<option value="1">10명 </option>
<option value="2">12명</option>
<option value="3">14명</option>
<option value="4">16명</option>
</select>
</div>
</div>

<div class="form-group row">
<label class="col-md-3 col-form-label">등록 관리자 </label>
<div class="col-md-9 col-form-label">
<div class="form-check">
<input class="form-check-input" id="radio1" type="radio" value="radio1" name="radios">
<label class="form-check-label" for="radio1">Option 1</label>
</div>
<div class="form-check">
<input class="form-check-input" id="radio2" type="radio" value="radio2" name="radios">
<label class="form-check-label" for="radio2">Option 2</label>
</div>
<div class="form-check">
<input class="form-check-input" id="radio3" type="radio" value="radio2" name="radios">
<label class="form-check-label" for="radio3">Option 3</label>
</div>
</div>
</div>

<div class="form-group row">
<label class="col-md-3 col-form-label">Inline Checkboxes</label>
<div class="col-md-9 col-form-label">
<div class="form-check form-check-inline mr-1">
<input class="form-check-input" id="inline-checkbox1" type="checkbox" value="check1">
<label class="form-check-label" for="inline-checkbox1">One</label>
</div>
<div class="form-check form-check-inline mr-1">
<input class="form-check-input" id="inline-checkbox2" type="checkbox" value="check2">
<label class="form-check-label" for="inline-checkbox2">Two</label>
</div>
<div class="form-check form-check-inline mr-1">
<input class="form-check-input" id="inline-checkbox3" type="checkbox" value="check3">
<label class="form-check-label" for="inline-checkbox3">Three</label>
</div>
</div>
</div>
</form>
</div>
<div class="form-group row">
<label class="col-md-3 col-form-label" for="textarea-input">등록 시  특이사항</label>
<div class="col-md-9">
<textarea class="form-control" id="textarea-input" name="textarea-input" rows="9" placeholder="우천 시 경기 취소.. & 풋살화 공급 제한 & 최소 경기 인원 & 기타 등등..."></textarea>
</div>

</div>
<button class="btn btn-block btn-primary" type="button" style="width:200px; float: right; color:primary;" @click="register()">등록하기</button> 
</div>
</div>
</div>

<div class="card-body" width:autocomplete text-align="center">
    <h3 class="card-title" >구장 등록 날짜 선택</h3>
 <v-date-picker 
  margin:auto
  v-model="picker"
  left
  selected-items-text:ko
  width="300" ></v-date-picker>
  <template>

<v-card
    width="300"
   left
   style="margin-top:20px;"
  >
    <v-list-item two-line>
      <v-list-item-content>
        <v-list-item-title class="headline">신촌 1경기장</v-list-item-title>
        <v-list-item-subtitle>{{picker}}</v-list-item-subtitle>
      </v-list-item-content>
    </v-list-item>
   <legend></legend>
    <v-card-text>
      <v-row align="center">
        <v-col class="display-3" cols="6">
          23&deg;C
        </v-col>
        <v-col cols="6">
          <v-img
            src="https://cdn.vuetifyjs.com/images/cards/sun.png"
            alt="Sunny image"
            width="92"
          ></v-img>
        </v-col>
      </v-row>
    </v-card-text>
    <v-list-item>
      <v-icon>mdi-send</v-icon><v-list-item-subtitle>풍속: 3m/s</v-list-item-subtitle>
    </v-list-item>
    <v-list-item>
      <v-icon>cloud</v-icon><v-list-item-title>강수 확률: 48%</v-list-item-title>
    </v-list-item>
    <v-slider
      v-model="time"
      :max="6"
      :tick-labels="labels"
      class="mx-4"
      ticks
    ></v-slider>
    <v-list class="transparent">
      <v-list-item
        v-for="item in forecast"
        :key="item.day"
      >
        <v-list-item-title>{{ item.day }}</v-list-item-title>
        <v-list-item-icon>
          <v-icon>{{ item.icon }}</v-icon>
        </v-list-item-icon>
        <v-list-item-subtitle class="text-right">
          {{ item.temp }}
        </v-list-item-subtitle>
      </v-list-item>
    </v-list>
    <v-divider></v-divider>
    <v-card-actions>
      <v-btn text>Full Report</v-btn>
    </v-card-actions>
  </v-card>
</template>
</div>
</v-row>
</v-app>
</template>
<script>
export default{
   data(){
      return{
         picker: new Date().toISOString().substr(0, 10),
         labels: ['일', '월', '화', '수', '목', '금', '토'],
            time: 0,
            forecast: [
            { day: 'Tuesday', icon: 'mdi-white-balance-sunny', temp: '24\xB0/12\xB0' },
            { day: 'Wednesday', icon: 'mdi-white-balance-sunny', temp: '22\xB0/14\xB0' },
            { day: 'Thursday', icon: 'mdi-cloud', temp: '25\xB0/15\xB0' },
            ]
      }
   },
   methods:{
      show(){
         this.$router.push({path:'/datepicker'})
      },
      register(){
         alert(this.picker)
      }
   }

}
</script>
<style scoped>

</style>