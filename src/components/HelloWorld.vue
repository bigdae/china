
/* eslint-disable */
<template>
  <div id="app">
    <v-app id="inspire">
      <v-container fluid :grid-list-md="!$vuetify.breakpoint.xs">
      <v-layout wrap row>
        <v-flex xs12 sm12>
          <v-card>
            <v-list subheader three-line>
              <template v-for="(item, index) in items">
                <v-subheader
                  v-if="item.header"
                  :key="item.header"
                >
                  {{ item.header }}
                </v-subheader>

 
                <v-list-tile
                  v-else
                  :key="item.title"
                  @click="playFile(item.mp3url, index)">

                  <v-list-tile-content>                
                    <v-list-tile-sub-title v-html="item.kor"></v-list-tile-sub-title>                    
                    <v-list-tile-sub-title v-html="item.subtitle"></v-list-tile-sub-title>
                  </v-list-tile-content>        
                </v-list-tile> 

                <v-divider :key="index"></v-divider>
                <!--
                <v-divider :key="index"></v-divider>
                <audio :key="index" ref="audio" :src="item.mp3url"></audio>
                <source :src="item.mp3url">>

                -->
                
                <audio :key="index" ref="audio">
                 <source :src="item.mp3url">
                </audio>
                
                
              </template>
            </v-list>
          </v-card>
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
      items: [
        { header: '복음' },
        {
          mp3url: require('../assets/1.mp3'),
          title: '神创造宇宙万物。',
          subtitle: "Shén chuàngzào yǔzhòu wànwù.",
          kor : "하나님께서 천지만물을 만드셨습니다."
        },
        {
          mp3url: require('../assets/2.mp3'),
          title: '包括我们人类。',
          subtitle: "bāokuò wǒmen rénlèi.",
          kor : "우리 인류를 포함해서요."
        },
        {
          mp3url: require('../assets/3.mp3'),
          title: '山上的树，田野的花 等。一个生命也不能自己随便出现的。',
          subtitle: "Shān shàng de shū, tiányě de huā děng. Yígè shēngmíng yě bùnéng zìjǐ suíbiàn chūxiàn de.",
          kor : "산의 나무, 들의 꽃 등. 어떠한 생명도 스스로 임의로 생겨날 수 없습니다."
        },
        {
          mp3url: require('../assets/4.mp3'),
          title: '创造这些的存在是上帝，唯一的神。',
          subtitle: "Chuàngzào zhè xiē de cúnzài shì shàngdì, wéiyī de shén.",
          kor : "이 모든 것을 창조한 존재는 유일한 신이신 하나님입니다."
        },
        {
          mp3url: require('../assets/5.mp3'),
          title: '原来上帝和我们的关系很好了。祂很爱我们。',
          subtitle: "Yuánlái shàngdì hé wǒmen de guānxi hěn hǎo le. Tā hěn ài wǒmen.",
          kor : "원래 하나님과 인간의 관계는 매우 좋았습니다. 그분은 우리를 매우 사랑하십니다"
        },
        {
          mp3url: require('../assets/6.mp3'),
          title: '但是人愿意随意生活,离开了上帝。祂说这是罪。',
          subtitle: "dànshì rén yuànyì suíyì shēnghuó, líkāi le shàngdì. tā shuō zhè shì zuì。",
          kor : "그러나 인간은 마음대로 살기를 원해서 하나님을 떠났습니다. 하나님은 이것을 죄라고 하십니다."
        },
        {
          mp3url: require('../assets/7.mp3'),
          title: '由于我们的犯罪，与上帝的关系隔绝了',
          subtitle: "Yóuyú wǒmen de fànzuì, yǔ shàngdì de guānxi géjué le",
          kor : "우리가 범죄함으로, 하나님과의 관계는 단절되었습니다."
        },
        {
          mp3url: require('../assets/8.mp3'),
          title: '以前的情况都变坏了, 终于罪叫人永远死亡。',
          subtitle: "Yǐqián de qíngkuàng dōu biànhuài le, zhōngyú zuì jiào rén yǒngyuǎn sǐwáng",
          kor : "이전의 상황은 완전히 나쁘게 변했고, 결국 죽음에 이르게 되었습니다"
        },
        {
          mp3url: require('../assets/9.mp3'),
          title: '所以人类要通过自己的努力与神再沟通。',
          subtitle: "Suǒyǐ rénlèi yào tōngguò zìjǐ de nǔlì yǔ shén zài gōutōng",
          kor : "그래서 인간은 자신의 노력으로 하나님과 다시 교제하려고 노력했습니다."
        },
        {
          mp3url: require('../assets/10.mp3'),
          title: '但是我们不能恢复以前的关系，喜乐。',
          subtitle: "dànshì wǒmen bùnéng huīfù yǐqián de guānxi, xǐlè",
          kor : "그러나 우리는 이전의 관계와 기쁨을 회복할 수 없었습니다"
        },
        {
          mp3url: require('../assets/11.mp3'),
          title: '因为带着自己的罪，通过自己的努力，不能与神沟通。',
          subtitle: "Yīnwèi dàizhe zìjǐ de zuì, tōngguò zìjǐ de nǔlì, bùnéng yǔ shén gōutōng",
          kor : "왜냐하면 자신의 죄를 가지고서, 자신의 노력으로는, 하나님과 교제할 수 없기 때문입니다"
        },
        {
          mp3url: require('../assets/12.mp3'),
          title: '为了解决这个罪的问题，祂给我们耶稣基督。',
          subtitle: "wèile jiějué zhège zuì de wèntí, tā gěi wǒmen yēsū jīdū",
          kor : "그래서 하나님께서는 이 죄의 문제를 해결하기 위해 예수님을 우리에게 주셨습니다"
        },
        {
          mp3url: require('../assets/13.mp3'),
          title: '耶稣代替我们的罪死在十字架上，三天以后复活了。',
          subtitle: "Yēsū dàitì wǒmen de zuì sǐ zài shízìjià shàng, sāntiān yǐhòu fùhuó le",
          kor : "예수님께서는 우리의 죄를 대신해서 십자가에서 죽으시고 3일 후에 부활하셨습니다."
        },
        {
          mp3url: require('../assets/14.mp3'),
          title: '耶稣成为上帝与人间的桥梁。',
          subtitle: "yēsū chéngwéi shàngdì yǔ rénjiān de qiáoliáng .",
          kor : "그분은 하나님과 우리 사이의 다리가 되어주신 것입니다."
        },                
        {
          mp3url: require('../assets/15.mp3'),
          title: '只是依靠这些事情,才能恢复与神亲密的关系。',
          subtitle: "zhǐshì yīkào zhèxiē shìqing, cáinéng huīfù yǔ shén qīnmì de guānxi.",
          kor : "오로지 이 사실을 믿어야, 하나님과 화목한 관계를 회복할 수 있습니다"
        },                
        {
          mp3url: require('../assets/16.mp3'),
          title: '得到永生，完美的喜乐。',
          subtitle: "dédào yǒngshēng, wánměi de xǐlè。",
          kor : "영생을 얻고 온전한 기쁨을 얻게 됩니다."
        },                
        {
          mp3url: require('../assets/17.mp3'),
          title: '怎么样?你能相信吗?/ 你能了解吗?',
          subtitle: "Zěnme yàng?nǐ néng xiāngxìn ma?/ nǐ néng liǎojiě ma?",
          kor : "어떻습니까? 당신은 믿을 수 있겠어요?/ 이해할 수 있겠어요?"
        },                
        {
          mp3url: require('../assets/18.mp3'),
          title: '你也能相信上帝，成为祂的儿女。',
          subtitle: "nǐ yě néng xiāngxìn shàngdì, chéngwéi tā de érnǚ",
          kor : "당신도 하나님을 믿고 그분의 자녀가 될 수 있습니다."
        },                
        {
          mp3url: require('../assets/19.mp3'),
          title: '有兴趣的话，请再看这个视频。',
          subtitle: "yǒu xìngqù de huà， qǐng zài kàn zhège shìpín。",
          kor : "관심이 있다면, 이 영상을 보기 바랍니다."
        },                
        {
          mp3url: require('../assets/20.mp3'),
          title: '愿意相信的话，跟我一起读祷告文。',
          subtitle: "yuànyì xiāngxìn de huà, gēn wǒ yìqǐ dú dǎogàowén。",
          kor : "믿기 원한다면, 나와 함께 기도문을 읽읍시다."
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
