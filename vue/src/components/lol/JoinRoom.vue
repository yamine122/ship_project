<template>
<div>
<v-app id="app">
  <v-content >
    <v-container class="float-md-left">
      <v-layout>
        <v-flex xs12 sm8 md4>
          <v-card id="ch" color="primary lighten-4">
            <v-toolbar dark color="primary darken-1">
              <v-toolbar-title>채팅</v-toolbar-title>
            </v-toolbar>
            <v-card-text>
        <v-list ref="chat" id="logs">
          <template v-for="(item, index) in logs">
            <v-subheader v-if="item" :key="index">{{ item }}</v-subheader>
          </template>
        </v-list>
            </v-card-text>
            <v-card-actions>
              <v-form @submit.prevent="submit">
              <v-text-field v-model="msg" label="Message" single-line solo-inverted></v-text-field>
              <v-btn fab dark small color="primary" type="submit">
                <v-icon dark>전송</v-icon>
              </v-btn>
                </v-form>
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
export default{
  data(){
    return {
      logs: [],
      msg: null
    }
  },
  methods: {
    submit() {
      this.logs.push(this.msg);
      this.msg = "";
    }
  },
  watch: {
    logs() {
      setTimeout(() => {
        this.$refs.chat.$el.scrollTop = this.$refs.chat.$el.scrollHeight;
      }, 0);
    }
  }
}
</script>
<style scoped>
#logs {
  height: 100px;
  overflow: auto;
}
#app{
  width: 100%;
  height: 100%;
  position: fixed;
}
#ch{
  width:80%;
  height:100%;
  position: left;
}

</style>