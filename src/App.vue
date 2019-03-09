<template>
  <div id="app">

    <v-tabs
      v-model="active"
      color="cyan"
      dark
      slider-color="yellow">

      <v-tabs-slider color="yellow"></v-tabs-slider>

      <v-tab ripple key="1" value="#tab-1">  
        중국어 복음
      </v-tab>
      <v-tab ripple key="2" value="#tab-2">  
        영어 복음
      </v-tab>


      <v-tabs-items>
        <v-tab-item>
          <v-card flat key="1" value="tab-1">  
            <China/>
          </v-card>
        </v-tab-item>
        <v-tab-item>
          <v-card flat key="2" value="tab-2">  
            <English/>
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
   