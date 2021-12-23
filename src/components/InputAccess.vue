<template>
  <a-space direction='vertical'>
    <Input :callback='callback' :lines="this.linesMap()" :stops="this.stopsMap()"></Input>
    <a-card title='你的路线' v-if="resultShow"  style="width:100%">
      <p>{{this.spanInfo(this.travel.start.line, this.travel.start.stop)}}
        <a-tag :color='this.linesInfo[this.travel.start.line].color'>{{this.travel.start.line}}</a-tag>
            <a-tag>{{this.travel.start.stop}}</a-tag>
            ➡️
            {{this.spanInfo(this.travel.end.line, this.travel.end.stop)}}
            <a-tag :color='linesInfo[this.travel.end.line].color'>{{this.travel.end.line}}</a-tag>
            <a-tag>{{this.travel.end.stop}}</a-tag>
      </p>
    </a-card>
  </a-space>
</template>

<script>
import Input from './Input.vue';

export default {
  name: 'InputAccess',
  props: ['linesInfo'],
  data: function() {
    return {
      travel: {
        start: {line: '1', stop: '1'},
        end: {line: '1', stop: '1'}
      },
      resultShow: false,
    }
  },

  components: {
    Input,
  },
  methods: {
    linesMap: function() {
      var result = []
      for (var item in this.linesInfo) {
        var obj = new Object()
        obj['value'] = item
        obj['label'] = this.linesInfo[item].name
        result.push(obj)
      }
      return result
    },

    stopsMap: function() {
      var result = new Object()
      for (var item in this.linesInfo) {
        result[item] = this.linesInfo[item].stops
      }
      return result
    },

    callback: function(pack) {
        this.travel.start.line = pack[0]
        this.travel.start.stop = pack[1]
        this.travel.end.line = pack[2]
        this.travel.end.stop = pack[3]
        this.resultShow = true
    },

    findByValue: function(value, arr) {
      var filtered = arr.filter(function(item) {return item.value === value})
      if (filtered.length) {return filtered[0].label}
    },

    spanInfo: function(line, stop) {
      return this.findByValue(stop, this.linesInfo[line].stops)
    }

  },
}
</script>

<style scoped>
* {
  text-align: center;
}
</style>