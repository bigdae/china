
/* eslint-disable */
<template>
  <div id="app">
    <v-app id="inspire">
      <v-container fluid :grid-list-md="!$vuetify.breakpoint.xs">
        <v-layout>
          <v-flex xs12 sm12 >

            <v-layout row wrap>
              <v-flex xs6>
                  <v-switch
                    v-model="playNextMusic"
                    :label="`Auto Next`"
                  ></v-switch> 
              </v-flex>
              <v-flex xs12 xs6>
                <v-btn absolute
                      dark
                      fab
                      middle
                      fixed
                      right
                      color="gray"
                      v-show="playingYn == 'Y' && playNextMusic == true"
                      @click="stop()">STOP</v-btn>
              </v-flex>
            </v-layout>

            <template v-for="(item, index) in items"> <!-- engItems -->
              <v-card :key="'content' + index">
           
                <v-card-title primary-title> 
                  <div :id="'messageDisplay' + index">
                    <div class="text-xs-left headline" 
                         @click="playFile(item.mp3url, index, 1)"
                         >{{item.title}}</div>
                    <div class="text-xs-left"
                         @click="playFile(item.mp3url, index, 1)"
                    > {{ item.kor }} </div>
                    <div class="text-xs-left mb-2" 
                         v-show="type !== 'eng'"
                         @click="playFile(item.mp3url, index, 0.7)"> {{ item.subtitle }} 
                         </div>  
                  </div>
                </v-card-title>
    
                <v-btn flat small v-show='item.subs'
                  @click="toggleButton(index)"
                >{{item.toggleText}}</v-btn>
                <v-divider :key="index+'div'"></v-divider>
              </v-card>
              <audio :key="'audio' + index" :ref="'audio' + index">
                 <source :src="item.mp3url">
              </audio>         

              
              <!-- sub item start-->
              <template v-for="(sub, sindex) in item.subs">
                <v-card :key="'contentsub' + sindex" color="#EFEFEF">

                  <v-card-title primary-title v-show=sub.show>
                    <div :id="'subMessageDisplay' + sindex">
                      <div class="text-xs-left headline" 
                          @click="playFile(sub.mp3url, index+'-'+sindex, 1)"
                          >{{sub.title}}</div>
                      <div class="text-xs-left"
                          @click="playFile(sub.mp3url, index+'-'+sindex, 1)"
                      > {{ sub.kor }} </div>
                      <div class="text-xs-left mb-2" 
                          v-show="type !== 'eng'"
                          @click="playFile(sub.mp3url, index+'-'+sindex, 0.7)"
                          > {{ sub.subtitle }} </div>  
                    </div>
                  </v-card-title>
                  <v-divider :key="sindex+'divs'" v-show=sub.show></v-divider>
                </v-card>
                <audio :key="'subaudio' + sindex" :ref="'audio' + index + '-' + sindex">
                  <source :src="sub.mp3url">
                </audio>         
              <!-- sub item end -->
                
                    
              </template>




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
      index : 0,
      playingYn : 'N',
      playNextMusic : false,
      items: [
        {
          mp3url: require('../assets/1.mp3'),
          title: '神创造了宇宙万物.',
          subtitle: "Shén chuàngzàole yǔzhòu wànwù",
          kor : "하나님께서 천지만물을 만드셨습니다."
        },
        {
          mp3url: require('../assets/2.mp3'),
          title: '包括我们人类.',
          subtitle: "bāokuò wǒmen rénlèi.",
          kor : "우리 인류를 포함해서요."
        },
        {
          mp3url: require('../assets/3.mp3'),
          title: '山上的树，田野的花等.一个生命也不能自己随便出现的.',
          subtitle: "Shān shàng de shù, tiányě de huā děng. Yígè shēngmìng yě bùnéng zìjǐ suíbiàn chūxiàn de.",
          kor : "산의 나무, 들의 꽃 등. 어떠한 생명도 스스로 임의로 생겨날 수 없습니다.",
          toggle : false,
          toggleText : '펼치기',               
          subs : [
            {
              mp3url: require('../assets/3-1.mp3'),
              title: '山上的树，田野的花等.',
              subtitle: "Shān shàng de shù, tiányě de huā děng.",
              kor : "산의 나무, 들의 꽃 등.",
              show : false,          
            },
            {
              mp3url: require('../assets/3-2.mp3'),
              title: '一个生命也不能自己随便出现的.',
              subtitle: "Yígè shēngmìng yě bùnéng zìjǐ suíbiàn chūxiàn de.",
              kor : "어떠한 생명도 스스로 임의로 생겨날 수 없습니다.",
              show : false,         
            },
          ]
        },
        {
          mp3url: require('../assets/4.mp3'),
          title: '创造这些存在的是上帝，唯一的神.',
          subtitle: "Chuàngzào zhèxiē cúnzài de shì shàngdì, wéiyī de shén",
          kor : "이 모든 것을 창조한 존재는 유일한 신이신 하나님입니다."
        },
        {
          mp3url: require('../assets/5.mp3'),
          title: '原来上帝和我们的关系很好.祂很爱我们.',
          subtitle: "Yuánlái shàngdì hé wǒmen de guānxì hěn hǎo. Tā hěn ài wǒmen.",
          kor : "원래 하나님과 인간의 관계는 매우 좋았습니다. 그분은 우리를 매우 사랑하십니다.",
          toggle : false,
          toggleText : '펼치기',                
          subs : [
            {
              mp3url: require('../assets/5-1.mp3'),
              title: '原来上帝和我们的关系很好.',
              subtitle: "Yuánlái shàngdì hé wǒmen de guānxì hěn hǎo.",
              kor : "원래 하나님과 인간의 관계는 매우 좋았습니다.",
              show : false,                
            },
            {
              mp3url: require('../assets/5-2.mp3'),
              title: '祂很爱我们.',
              subtitle: "Tā hěn ài wǒmen.",
              kor : "그분은 우리를 매우 사랑하십니다.",
              show : false,            
            },
          ]          
        },
        {
          mp3url: require('../assets/6.mp3'),
          title: '但是人愿意随意生活,离开了上帝.祂说这是罪.',
          subtitle: "dànshì rén yuànyì suíyì shēnghuó, líkāi le shàngdì. tā shuō zhè shì zuì.",
          kor : "그러나 인간은 마음대로 살기를 원해서 하나님을 떠났습니다. 하나님은 이것을 죄라고 하십니다.",
          toggle : false,
          toggleText : '펼치기',                
          subs : [
            {
              mp3url: require('../assets/6-1.mp3'),
              title: '但是人愿意随意生活,离开了上帝.',
              subtitle: "dànshì rén yuànyì suíyì shēnghuó, líkāi le shàngdì.",
              kor : "그러나 인간은 마음대로 살기를 원해서 하나님을 떠났습니다.",
              show : false,                
            },
            {
              mp3url: require('../assets/6-2.mp3'),
              title: '祂说这是罪.',
              subtitle: "tā shuō zhè shì zuì.",
              kor : "하나님은 이것을 죄라고 하십니다.",
              show : false,            
            },
          ]             
        },
        {
          mp3url: require('../assets/7.mp3'),
          title: '由于我们的罪，与上帝的关系隔绝了.',
          subtitle: "Yóuyú wǒmen de zuì, yǔ shàngdì de guānxì géjué le.",
          kor : "우리가 범죄함으로, 하나님과의 관계는 단절되었습니다.",
          toggle : false,
          toggleText : '펼치기',                
          subs : [
            {
              mp3url: require('../assets/7-1.mp3'),
              title: '由于我们的罪,',
              subtitle: "Yóuyú wǒmen de zuì,",
              kor : "우리가 범죄함으로,",
              show : false,                
            },
            {
              mp3url: require('../assets/7-2.mp3'),
              title: '与上帝的关系隔绝了.',
              subtitle: "yǔ shàngdì de guānxì géjué le.",
              kor : "하나님과의 관계는 단절되었습니다.",
              show : false,            
            },
          ]                   
        },
        {
          mp3url: require('../assets/8.mp3'),
          title: '以前的情况都变坏了, 终于罪叫人永远死亡.',
          subtitle: "Yǐqián de qíngkuàng dōu biàn huài le, zhōngyú zuì jiào rén yǒngyuǎn sǐwáng.",
          kor : "이전의 상황은 완전히 나쁘게 변했고, 결국 죽음에 이르게 되었습니다.",
          toggle : false,
          toggleText : '펼치기',                
          subs : [
            {
              mp3url: require('../assets/8-1.mp3'),
              title: '以前的情况都变坏了,',
              subtitle: "Yǐqián de qíngkuàng dōu biàn huài le,",
              kor : "이전의 상황은 완전히 나쁘게 변했고,",
              show : false,                
            },
            {
              mp3url: require('../assets/8-2.mp3'),
              title: '终于罪叫人永远死亡.',
              subtitle: "zhōngyú zuì jiào rén yǒngyuǎn sǐwáng.",
              kor : "결국 죽음에 이르게 되었습니다.",
              show : false,            
            },         
          ] 
        },
        {
          mp3url: require('../assets/9.mp3'),
          title: '所以人类要通过自己的努力与神再沟通.',
          subtitle: "Suǒyǐ rénlèi yào tōngguò zìjǐ de nǔlì yǔ shén zài gōutōng",
          kor : "그래서 인간은 자신의 노력으로 하나님과 다시 교제하려고 노력했습니다."
        },
        {
          mp3url: require('../assets/10.mp3'),
          title: '但是我们不能恢复以前的关系，喜乐.',
          subtitle: "dànshì wǒmen bùnéng huīfù yǐqián de guānxi, xǐlè",
          kor : "그러나 우리는 이전의 관계와 기쁨을 회복할 수 없었습니다"
        },
        {
          mp3url: require('../assets/11.mp3'),
          title: '因为带着自己的罪，通过自己的努力，不能与神沟通.',
          subtitle: "Yīnwèi dàizhe zìjǐ de zuì, tōngguò zìjǐ de nǔlì, bùnéng yǔ shén gōutōng",
          kor : "왜냐하면 자신의 죄를 가지고서, 자신의 노력으로는, 하나님과 교제할 수 없기 때문입니다.",
          toggle : false,
          toggleText : '펼치기',                
          subs : [
            {
              mp3url: require('../assets/11-1.mp3'),
              title: '因为带着自己的罪,',
              subtitle: "Yīnwèi dàizhe zìjǐ de zuì,",
              kor : "왜냐하면 자신의 죄를 가지고서,",
              show : false,                
            },
            {
              mp3url: require('../assets/11-2.mp3'),
              title: '通过自己的努力,',
              subtitle: "tōngguò zìjǐ de nǔlì,",
              kor : "자신의 노력으로는,",
              show : false,            
            },
            {
              mp3url: require('../assets/11-3.mp3'),
              title: '不能与神沟通.',
              subtitle: "bùnéng yǔ shén gōutōng.",
              kor : "하나님과 교제할 수 없기 때문입니다.",
              show : false,            
            },            
          ]              
        },
        {
          mp3url: require('../assets/12.mp3'),
          title: '为了解决这个罪的问题，祂给我们耶稣基督.',
          subtitle: "wèile jiějué zhège zuì de wèntí, tā gěi wǒmen yēsū jīdū.",
               // Wèi liǎo jiějué zhège zuì de wèntí, tā gěi wǒmen yēsū jīdū
          kor : "그래서 하나님께서는 이 죄의 문제를 해결하기 위해, 예수님을 우리에게 주셨습니다.",
          toggle : false,
          toggleText : '펼치기',                
          subs : [
            {
              mp3url: require('../assets/12-1.mp3'),
              title: '为了解决这个罪的问题,',
              subtitle: "wèile jiějué zhège zuì de wèntí,",
              kor : "그래서 하나님께서는 이 죄의 문제를 해결하기 위해,",
              show : false,                
            },
            {
              mp3url: require('../assets/12-2.mp3'),
              title: '祂给我们耶稣基督.',
              subtitle: "tā gěi wǒmen yēsū jīdū.",
              kor : "예수님을 우리에게 주셨습니다.",
              show : false,            
            },
          ]          
        },
        {
          mp3url: require('../assets/13.mp3'),
          title: '耶稣代替我们的罪死在十字架上，三天以后复活了.',
          subtitle: "Yēsū dàitì wǒmen de zuì sǐ zài shízìjià shàng, sāntiān yǐhòu fùhuó le.",
          kor : "예수님께서는 우리의 죄를 대신해서 십자가에서 죽으시고, 3일 후에 부활하셨습니다.",
          toggle : false,
          toggleText : '펼치기',                
          subs : [
            {
              mp3url: require('../assets/13-1.mp3'),
              title: '耶稣代替我们的罪死在十字架上,',
              subtitle: "Yēsū dàitì wǒmen de zuì sǐ zài shízìjià shàng,",
              kor : "예수님께서는 우리의 죄를 대신해서 십자가에서 죽으시고,",
              show : false,                
            },
            {
              mp3url: require('../assets/13-2.mp3'),
              title: '三天以后复活了.',
              subtitle: "sāntiān yǐhòu fùhuó le.",
              kor : "3일 후에 부활하셨습니다.",
              show : false,            
            },       
          ]   
        },
        {
          mp3url: require('../assets/14.mp3'),
          title: '耶稣成为上帝与人间的桥梁.',
          subtitle: "yēsū chéngwéi shàngdì yǔ rénjiān de qiáoliáng .",
          kor : "그분은 하나님과 우리 사이의 다리가 되어주신 것입니다."
        },                
        {
          mp3url: require('../assets/15.mp3'),
          title: '只有相信这个事实,才能恢复与神亲密的关系.',
          subtitle: "Zhǐyǒu xiāngxìn zhège shìshí, cáinéng huīfù yǔ shén qīnmì de guānxì.",
          kor : "이 사실을 믿음으로써만, 하나님과 화목한 관계를 회복할 수 있습니다.",
          toggle : false,
          toggleText : '펼치기',                
          subs : [
            {
              mp3url: require('../assets/15-1.mp3'),
              title: '只有相信这个事实,',
              subtitle: "Zhǐyǒu xiāngxìn zhège shìshí,",
              kor : "이 사실을 믿음으로써만",
              show : false,                
            },
            {
              mp3url: require('../assets/15-2.mp3'),
              title: '才能恢复与神亲密的关系.',
              subtitle: "cáinéng huīfù yǔ shén qīnmì de guānxì.",
              kor : "하나님과 화목한 관계를 회복할 수 있습니다.",
              show : false,            
            },       
          ]             
        },                
        {
          mp3url: require('../assets/16.mp3'),
          title: '得到永生，完美的喜乐.',
          subtitle: "dédào yǒngshēng, wánměi de xǐlè.",
          kor : "영생을 얻고, 온전한 기쁨을 얻게 됩니다.",
          toggle : false,
          toggleText : '펼치기',                
          subs : [
            {
              mp3url: require('../assets/16-1.mp3'),
              title: '得到永生,',
              subtitle: "dédào yǒngshēng,",
              kor : "영생을 얻고,",
              show : false,                
            },
            {
              mp3url: require('../assets/16-2.mp3'),
              title: '完美的喜乐.',
              subtitle: "wánměi de xǐlè.",
              kor : "온전한 기쁨을 얻게 됩니다.",
              show : false,            
            },       
          ]      
        },                
        {
          mp3url: require('../assets/17.mp3'),
          title: '怎么样?你能相信吗?/ 你能了解吗?',
          subtitle: "Zěnme yàng?nǐ néng xiāngxìn ma?/ nǐ néng liǎojiě ma?",
          kor : "어떻습니까? 당신은 믿을 수 있겠어요?/ 이해할 수 있겠어요?",
          toggle : false,
          toggleText : '펼치기',                
          subs : [
            {
              mp3url: require('../assets/17-1.mp3'),
              title: '怎么样?你能相信吗?',
              subtitle: "Zěnme yàng?nǐ néng xiāngxìn ma?",
              kor : "어떻습니까? 당신은 믿을 수 있겠어요?",
              show : false,                
            },
            {
              mp3url: require('../assets/17-2.mp3'),
              title: '你能了解吗?',
              subtitle: "nǐ néng liǎojiě ma?",
              kor : "이해할 수 있겠어요?",
              show : false,            
            },       
          ]      
        },                
        {
          mp3url: require('../assets/18.mp3'),
          title: '你也能相信上帝，成为祂的儿女.',
          subtitle: "nǐ yě néng xiāngxìn shàngdì, chéngwéi tā de érnǚ.",
          kor : "당신도 하나님을 믿고 그분의 자녀가 될 수 있습니다.",
          toggle : false,
          toggleText : '펼치기',                
          subs : [
            {
              mp3url: require('../assets/18-1.mp3'),
              title: '你也能相信上帝,',
              subtitle: "nǐ yě néng xiāngxìn shàngdì,",
              kor : "당신도 하나님을 믿고",
              show : false,                
            },
            {
              mp3url: require('../assets/18-2.mp3'),
              title: '成为祂的儿女.',
              subtitle: "chéngwéi tā de érnǚ.",
              kor : "그분의 자녀가 될 수 있습니다.",
              show : false,            
            },       
          ]
        },   
        {
          mp3url: require('../assets/19.mp3'),
          title: '有兴趣的话，请再看这个视频.',
          subtitle: "yǒu xìngqù de huà， qǐng zài kàn zhège shìpín.",
          kor : "관심이 있다면, 이 영상을 보기 바랍니다.",
          toggle : false,
          toggleText : '펼치기',                
          subs : [
            {
              mp3url: require('../assets/19-1.mp3'),
              title: '有兴趣的话,',
              subtitle: "yǒu xìngqù de huà，",
              kor : "관심이 있다면,",
              show : false,                
            },
            {
              mp3url: require('../assets/19-2.mp3'),
              title: '请再看这个视频.',
              subtitle: "qǐng zài kàn zhège shìpín.",
              kor : "이 영상을 보기 바랍니다.",
              show : false,            
            },       
          ]
        },
        {
          mp3url: require('../assets/20.mp3'),
          title: '愿意相信的话，跟我一起读祷告文.',
          subtitle: "yuànyì xiāngxìn de huà, gēn wǒ yìqǐ dú dǎogàowén.",
          kor : "믿기 원한다면, 나와 함께 기도문을 읽읍시다.",
          toggle : false,
          toggleText : '펼치기',                
          subs : [
            {
              mp3url: require('../assets/20-1.mp3'),
              title: '愿意相信的话,',
              subtitle: "yuànyì xiāngxìn de huà,",
              kor : "믿기 원한다면,",
              show : false,                
            },
            {
              mp3url: require('../assets/20-2.mp3'),
              title: '跟我一起读祷告文.',
              subtitle: "gēn wǒ yìqǐ dú dǎogàowén.",
              kor : "나와 함께 기도문을 읽읍시다.",
              show : false,            
            },       
          ]
        },                

      ],
      previousMusicIndex : -1
    }
  },
  methods :  {
    playFile(file, index, rate) {
        this.index = index;      
        if ( this.previousMusicIndex > 0 && this.previousMusicIndex < this.items.length ) {
          //var musicForStop = this.$refs.audio[this.previousMusicIndex];
          var musicForStop = this.$refs['audio' + this.previousMusicIndex][0];
          musicForStop.pause();
          musicForStop.currentTime = 0;
          this.playingYn = 'N'
        }
        this.previousMusicIndex = index;
        //var music = this.$refs.audio[index];
        var music = this.$refs['audio'+index][0]
        if ( music == undefined ) return;        
        if(music.paused){
            music.playbackRate = rate;
            music.play();
            this.playingYn = 'Y'
            var _this = this;
            music.onended = function() {
              if (_this.playNextMusic == false) {
                return;
              }
              //var nextMusic = _this.$refs.audio[index+1];
              var nextMusic = _this.$refs['audio' +(index+1)][0];
              _this.playFile(nextMusic, index+1, rate)
              _this.$vuetify.goTo('#messageDisplay' + index)
              
            }
        }else{
            music.pause();
            this.playingYn = 'N'
        }
    }, 
    stop() {
      //var music = this.$refs.audio[this.index];
      var music = this.$refs['audio' + this.index][0];
      music.pause()
      this.playingYn = 'N'
      music.currentTime = 0;

    },
    toggleButton(index){
      this.items[index].toggle = !this.items[index].toggle
      this.items[index].toggleText = this.items[index].toggle == false ? "펼치기" : "접기";
      for(var i in this.items[index].subs) {  
        this.items[index].subs[i].show = this.items[index].toggle
      }
    }
  }
}
</script>
