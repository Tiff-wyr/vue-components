<template>
  <div id="app">
    <count :num="number" :maxNum=10 :minNum=0 @count="getRes"></count>
    <mySwitch :active=" '按年付费' " inactive="按月付费" v-model="isSwitch"></mySwitch>
  </div>
</template>

<script>
  //绑定的是变量或表达式 v-bind
  import count from './components/count';
  import mySwitch from './components/mySwitch';

export default {
  name: 'App',
  data(){
    return {
      number:2,
      isSwitch:true
    }
  },
  methods:{
    getRes(res){
      this.number=res
    }
  },
  components:{
    count,
    mySwitch
  }
}
</script>

<style>
#app {
  margin: 0;
  padding: 0;
}
</style>
