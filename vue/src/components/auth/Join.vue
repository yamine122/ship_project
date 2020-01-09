<template>
<div id="app">
  <v-btn color="blue" dark fixed center @click="dialog = !dialog"> join </v-btn>
    <v-dialog v-model="dialog" width="550px">
      <v-card>
        <v-card-title class="blue darken-2" style="font-color:white" > CREATE ACCOUNT </v-card-title>
        
  <v-container>   
    <v-layout justify-center >
      <v-flex >
        
          <v-form>
            <v-container >
              <v-layout wrap justify-center>

                <v-flex  md8 style="padding:0px;">
                <v-text-field style="margin:0px;" v-validate="'required|max:10'" :counter="10" required
                center v-model="userid" label="ID" ></v-text-field>
                </v-flex>

                <v-flex xs8 md8 style="padding:0px;">
                <v-text-field type="password" style="margin:0px;" label="PASSWORD" v-model="passwd"></v-text-field>
                </v-flex>

                <v-flex xs8 md8 style="padding:0px;">
                <v-text-field style="margin:0px;" label="NAME" class="purple-input"></v-text-field>
                </v-flex>

            <v-flex xs8 md8 style="padding:0px;">
                <v-text-field style="margin:0px;" label="JOB"></v-text-field>
            </v-flex>

            <v-flex xs8 md8 style="padding:0px;" >
              <v-menu ref="startMenu" :close-on-content-click="false" offset-y
                :return-value.sync="trip.start" min-width="290px">
                <template v-slot:activator="{ on }">
                  <v-text-field v-model="trip.start" label="BIRTHDAY" 
                  readonly v-on="on"></v-text-field>
                </template>
                <v-date-picker v-model="date" no-title scrollable>
                  <v-spacer></v-spacer>
                  <v-btn text color="primary" @click="$refs.startMenu.save(date)">
                    OK</v-btn>
                  <v-btn text color="primary" @click="$refs.startMenu.isActive = false">
                    Cancel</v-btn>
                </v-date-picker>
              </v-menu>
            </v-flex>

          <v-flex xs8 md8>
            <v-select
                    :items="['0-17', '18-29', '30-54', '54+']"
                    label="AGE"
                    required
            ></v-select>
          </v-flex>

          <v-flex xs8 md8> 
             <v-autocomplete
                    :items="['Skiing', 'Ice hockey', 'Soccer', 'Basketball', 'Hockey', 'Reading', 'Writing', 'Coding', 'Basejump']"
                    label="INTERESTS"
                    multiple
            ></v-autocomplete>
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
         date: null,
      trip: {
      name: '',
      location: null,
      start: null,
      end: null,
    },
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