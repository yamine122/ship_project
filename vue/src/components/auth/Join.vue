<template>
<div id="app">
  <v-btn color="blue" dark fixed center @click="dialog = !dialog"> join </v-btn>
    <v-dialog v-model="dialog" width="800px">
      <v-card>
        <v-card-title class="blue darken-2" style="font-color:white" > CREATE ACCOUNT </v-card-title>
        
  <v-container>   
    <v-layout justify-center >
      <v-flex xs20 md10>
        
          <v-form>
            <v-container >
              <v-layout wrap>

                <v-flex xs12 sm6 style="padding:0px;">
                <v-text-field style="margin:0px;" v-validate="'required|max:10'" :counter="10" required
                center v-model="userid" label="ID" ></v-text-field>
                </v-flex>

                <v-flex xs12 md7 style="padding:0px;">
                <v-text-field style="margin:0px;" label="PASSWORD" v-model="passwd"></v-text-field>
                </v-flex>

                <v-flex xs12 md6 style="padding:0px;">
                <v-text-field style="margin:0px;" label="NAME" class="purple-input"></v-text-field>
                </v-flex>

            <v-flex xs12 style="padding:0px;">
                <v-text-field style="margin:0px;" label="JOB"></v-text-field>
            </v-flex>

            <v-flex xs12 style="padding:0px;">
              <v-text-field style="margin:0px;" type="date" label="BIRTHDAY" placeholder="1">
              </v-text-field>
            </v-flex>

              </v-layout>
            </v-container>
          </v-form>
        
      </v-flex>
    </v-layout>
  </v-container>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn text color="primary" @click="dialog = false">Submit</v-btn>
          <v-btn text color="error" @click="dialog = false">Cancel</v-btn>
        </v-card-actions>

    </v-card>
  </v-dialog>
</div>
</template>
<script>
export default {
    name: 'join',
    data () {
		return {
    dialog:false,
    name: '',
    email: '',
    select: null,
    items: [
      'Item 1',
      'Item 2',
      'Item 3',
      'Item 4',
    ],
    checkbox: null,
    dictionary: {
      attributes: {
        email: 'E-mail Address',
        // custom attributes
      },
      custom: {
        name: {
          required: () => '이름을 입력해야 합니다',
          max: '이름을 10자를 초과할 수 없습니다',
          // custom messages
        },
        select: {
          required: 'Select field is required',
        },
      },
    },
    }
  }
}
</script>

<style scoped>
@import 'https://fonts.googleapis.com/css?family=Montserrat|Open+Sans';
.theme--light.v-card{
  color:white;
}
div.flex{
  
}
</style>
