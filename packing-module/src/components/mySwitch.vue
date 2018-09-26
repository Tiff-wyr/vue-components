<template>
    <div class="switch-wrapper">
      <span :class="isdir ? 'text-color':''">{{activeText}}</span>
      <div :class="isdir ? 'bot-wrapper active':'bot-wrapper inactive'" @click="switchBall">
        <div :class="isdir ? 'ball ball-left':'ball ball-right'">
        </div>
      </div>
      <span :class="!isdir ? 'text-color':''">{{inactiveText}}</span>
    </div>
</template>

<script>
    export default {
      name: "mySwitch",
      props:{
        active:'',
        inactive:'',
        value:''
      },
      data(){
        return {
          activeText:this.active,
          inactiveText:this.inactive,
          isdir:this.value
        }
      },
      methods:{
        switchBall(){
          this.isdir=!this.isdir
          this.$emit('input',this.isdir)
        }
      },
    }
</script>

<style scoped>
.switch-wrapper{
  display: flex;
}
.switch-wrapper span{
  font-size: 14px;
}
.text-color{
  color:#35aff8
}
  .bot-wrapper{
    position: relative;
    margin: 0 10px;
    display: inline-block;
    width: 35px;
    height: 18px;
    padding: 2px;
    border-radius: 10px;
    cursor: pointer;
  }
.active {
  background: #13ce66;
  transition: all ease-in .1s;
}
.inactive {
  background: #ff4949;
  transition: all ease-in .1s;
}
.ball{
  position: absolute;
  width: 18px;
  height: 18px;
  border-radius: 50%;
  background: #fff;
}
  .ball-left{
    left:2px;
    transition:  all ease-in 0.2s;
  }
  .ball-right{
    left: 18px;
    transition:  all ease-in 0.2s;
  }

</style>
