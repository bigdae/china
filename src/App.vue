<template>
  <div id="app">

    <v-tabs
      color="cyan"
      dark
      slider-color="yellow">

      <v-tabs-slider color="yellow"></v-tabs-slider>

      <v-tab ripple key="1" value="#tab-1" @click="stopPlaying()">  
        중국어 버전
      </v-tab>
      <v-tab ripple key="2" value="#tab-2" @click="stopPlaying()">  
        영어 버전
      </v-tab>
 
      <v-tabs-items>
        <v-tab-item>
          <v-card flat key="1" value="tab-1">  
            <China ref="china"/>
          </v-card>
        </v-tab-item>
        <v-tab-item>
          <v-card flat key="2" value="tab-2">  
            <English ref="english"/>
          </v-card>
        </v-tab-item>        
      </v-tabs-items>      

    </v-tabs>
    
        

    
  </div>
</template>

<script>
import China from './components/China.vue'
import English from './components/English.vue'

export default {
  name: 'app',
  components: {
    China, English
  },   
  methods :  {
     stopPlaying() {
       this.$refs.china.stop()
       this.$refs.english.stop()
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
   