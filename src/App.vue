<template>
  <a-row align='middle'>
    <a-col :span='8'>
      <img src="https://cs.gzmtr.com/ckfw/xlu_2020/202011/W020211101558961941389.jpg" class="metro"> 
    </a-col>
    <a-col :span='8' :offset='6'>
    <a-space direction='vertical' class='main'>
      <input-access :linesInfo="linesInfo"></input-access>
      <result-displayer></result-displayer>
    </a-space>
  </a-col> 
  </a-row>
  
</template>

<script>
import InputAccess from './components/InputAccess.vue'
import ResultDisplayer from './components/ResultDisplayer.vue'
export default {
  name: 'App',
  components: {
    InputAccess,
    ResultDisplayer
  },
  data: function() {
    return {
      linesInfo: {
        '1': {
          name: '一号线',
          stops: [{value:'1', label:'广州东站'},{value:'2', label:'体育中心'},{value:'3', label:'体育西路'}],
          color: '#EECF2D',
        },
        '2': {
          name: '二号线',
          stops: [{value:'1', label:'广州南站'},{value:'2', label:'石壁'},{value:'4', label:'洛溪'}],
          color: '#005E9E'
        },
        '3': {
          name: '三号线',
          stops: [{value:'1', label:'机场北(T2)'},{value:'2', label:'机场南(T1)'},{value:'3', label:'高增'},{value:'4', label:'广州东站'}],
          color: '#EB9A3E'
        },
        '18': {
          name: '十八号线',
          stops: [{value:'1', label:'万顷沙'},{value:'2', label:'横沥'},{value:'3', label:'番禺广场'},{value:'4', label:'南村万博'},{value:'5', label:'沙溪'}],
          color: '#2A459C'
        },
        'GF': {
          name: '广佛线',
          stops: [{value:'1', label:'新城东'},{value:'2', label:'魁奇路'},{value:'3', label:'南洲'},{value:'4', label:'沥滘'}],
          color: '#BAD200'
        },
        'APM': {
          name: 'APM线',
          stops: [{value:'1', label:'广州塔'},{value:'2', label:'海心沙'},{value:'3', label:'大剧院'}],
          color: '#01B6E3'
        }
      },

      bestTime: [{line: '1', stop: '2'},
                 {line: '1', stop: '1'},
                 {line: '3', stop: '4'},
                 {line: '3', stop: '1'}]
    }
  }
}
</script>

<style>
#app {
  font-family: JetBrains mono, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}

input-access {
  text-align: start;
}

.metro {
  max-width: 600px;
  margin: 10px;
}
</style>
