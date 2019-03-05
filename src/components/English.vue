
/* eslint-disable */
<template>
  <div id="app">
    <v-app id="inspire">
      <v-container fluid :grid-list-md="!$vuetify.breakpoint.xs">
        <v-layout>
          <v-flex xs12 sm6 offset-sm3>

        <v-toolbar color="blue" dark>
          <v-toolbar-title>복음</v-toolbar-title>
          <v-spacer></v-spacer>
        </v-toolbar>


            <template v-for="(item, index) in items"> <!-- engItems -->
              <v-card :key="item.header"
              @click="playFile(item.mp3url, index)">
           
                <v-img
                  src="https://cdn.vuetifyjs.com/images/cards/desert.jpg"
                  aspect-ratio="2.75" v-show="imageShow == 'true'"
                ></v-img>


                <v-card-title primary-title>

                  <div>
                    <div class="text-xs-left" v-bind:class="{'headline':type!='eng'}">{{item.title}}</div>
                    <div class="text-xs-left"> {{ item.kor }} </div>
                    <div class="text-xs-left mb-2" v-show="type !== 'eng'"> {{ item.subtitle }} </div>  
                  </div>
                </v-card-title>
                <v-divider :key="index+'div'"></v-divider>
              </v-card>
                <audio :key="index" ref="audio">
                 <source :src="item.mp3url">
                </audio>              
            </template>

            
            
            <v-footer class="pa-3">
              <v-spacer></v-spacer>
              <div>&copy; {{ new Date().getFullYear() }}</div>
            </v-footer>            
          </v-flex>
        </v-layout>
      </v-container>
    </v-app>
  </div> 
</template>

<script>

export default {
  name: 'App',
  components: {
  
  },
  data () {
    return {
      type : 'china',
      imageShow : 'false',
      items : [
        {
          mp3url: require('../assets/50.mp3'),
          title: 'God created the world.',
          kor : "하나님은 세상을 창조하셨습니다."
        },    
        {
          mp3url: require('../assets/51.mp3'),
          title: 'When God created human beings, they had a good relationship.',
          kor : "신이 인간을 창조 할 때, 그들은 좋은 관계에 있었습니다."
        },    
        {
          mp3url: require('../assets/52.mp3'),
          title: 'hen one day, the first human being, Adam, committed a sin.',
          kor : "언젠가 첫번째 인간인 아담이 죄를 범했습니다."
        },    
        {
          mp3url: require('../assets/53.mp3'),
          title: 'What is a sin? A sin is disobedience and distrust towards God.',
          kor : "죄는 무엇입니까? 죄는 불순종이며 하나님을 불신합니다."
        },    
        {
          mp3url: require('../assets/54.mp3'),
          title: 'Human beings have sins in their hearts, such as corruption, arrogance, and jealousy.',
          kor : "인간은 부패, 오만, 질투와 같은 그들의 마음에 죄를 지니고 있습니다."
        },    
        {
          mp3url: require('../assets/55.mp3'),
          title: 'We all have sins deep in our minds. Since we have sins, we will surely die.',
          kor : "우리 모두는 우리의 마음 속에 깊은 죄를 가지고 있습니다. 우리에게는 죄가 있기 때문에 반드시 죽을 것입니다.."
        },    
        {
          mp3url: require('../assets/56.mp3'),
          title: 'We are all sinners. No one can avoid death.',
          kor : "우리는 모두 죄입니다. 누구도 죽음을 피할 수 없습니다."
        },    
        {
          mp3url: require('../assets/57.mp3'),
          title: 'However, God loved us so much that he sent Jesus Christ before us.',
          kor : "그러나 하나님은 우리를 사랑하셔서 그 아들을 이 세상에 보내주셨습니다."
        },    
        {
          mp3url: require('../assets/58.mp3'),
          title: 'Who is Jesus Christ? Jesus is the only son of God, and he has no sins at all.',
          kor : "예수 그리스도는 누구입니까? 예수님은 하나님의 유일한 아들 이시고, 그는 전혀 죄가 없습니다."
        },    
        {
          mp3url: require('../assets/59.mp3'),
          title: 'His name is another name for God.',
          kor : "그의 이름은 하나님의 다른 이름입니다."
        },    
        {
          mp3url: require('../assets/60.mp3'),
          title: 'On the cross, Jesus died for our sins. But he rose from the dead in three days.',
          kor : "십자가에서 예수님은 우리의 죄를 위해 죽으셨습니다. 그러나 그는 사흘 만에 죽음에서 부활했다."
        },    
        {
          mp3url: require('../assets/61.mp3'),
          title: 'If he hadn’t returned from death, I wouldn’t believe in him.',
          kor : "그가 죽음에서 돌아 오지 않았다면 나는 그를 믿지 않을 것입니다."
        },    
        {
          mp3url: require('../assets/62.mp3'),
          title: 'Jesus is the way, truth, and life.',
          kor : "예수님은 길과 진리와 삶입니다."
        },    
        {
          mp3url: require('../assets/63.mp3'),
          title: 'If you believe in Jesus, you will go to heaven where there is eternal life.',
          kor : "당신이 예수님을 믿는다면, 당신은 영원한 생명이있는 천국에 갈 것입니다."
        },    
        {
          mp3url: require('../assets/64.mp3'),
          title: 'You will enter God’s kingdom through Jesus.',
          kor : "당신은 예수님을 통해 하나님의 왕국에 들어갈 것입니다."
        },    
        {
          mp3url: require('../assets/65.mp3'),
          title: 'He is knocking on the door of your heart.',
          kor : "그는 당신의 마음 문을 두드리고 있습니다."
        },    
        {
          mp3url: require('../assets/66.mp3'),
          title: 'You can simply open the door and welcome him as a savior of your life.',
          kor : "당신은 단순히 문을 열고 당신의 삶의 구원자로서 그를 환영 할 수 있습니다."
        },    
        {
          mp3url: require('../assets/67.mp3'),
          title: 'Do you want to believe in Jesus Christ?',
          kor : "당신은 예수 그리스도를 믿고 싶습니까?"
        },          
      ],
      previousMusicIndex : -1
    }
  },
  methods :  {
    playFile(file, index) {
        if ( this.previousMusicIndex > 0 ) {
          var musicForStop = this.$refs.audio[this.previousMusicIndex];
          musicForStop.pause();
          musicForStop.currentTime = 0;
        }
        this.previousMusicIndex = index;
        var music = this.$refs.audio[index];
        if(music.paused){
            music.play();
        }else{
            music.pause();
        }
    }
  }
}
</script>
