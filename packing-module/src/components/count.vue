<template>
  <div class="count">
    <button @click="sub" :class="btnLeft ? 'btn btn-a':'btn'" :disabled="btnLeft">-</button>
    <input type="text" v-model="number">
    <button @click="add" :class="btnRight ? 'btn btn-a':'btn'" :disabled="btnRight">+</button>
  </div>
</template>

<script>
  export default {
    name: "count",
    props:{
      num:{
        type:Number
      },
      minNum:{
        type:Number,
        default:Math.min()
      },
      maxNum:{
        type:Number,
        default:Math.max()
      },
    },
    data() {
      return {
        number:this.num,
        maxNum:this.maxNum,
        minNum:this.minNum,
        btnLeft:false,
        btnRight:false

      }
    },
    watch: {
      number (value, oldValue) {
        if (value <= this.minNum) {
          this.number = this.minNum
          this.btnLeft = true
        } else if (value >= this.maxNum) {
          this.number = this.maxNum
          this.btnRight = true
        } else {
          this.btnLeft = false
          this.btnRight = false
        }
      }
    },
    methods: {
      sub() {
        this.number--
        this.$emit('count',this.number)
      },
      add() {
        this.number++
        this.$emit('count',this.number)
      },
    },
    created(){
      if(this.number<=this.minNum){
        this.btnLeft=true
      }else if(this.number>=this.maxNum){
        this.btnRight=true
      }
    }
  }
</script>

<style scoped>
  *{
    margin: 0;
    padding: 0;
  }
.count{
  width: 120px;
  height: 50px;
  margin:20px 40px;
  border: 1px solid #e1e1e1;
  border-radius: 6px;
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding: 0;
  overflow: hidden;
}
  .count:hover {
    border-color: #409eff;
  }
.count input{
  width: 40px;
  height: 40px;
  text-align: center;
  border: none;
}
  .btn{
    width: 40px;
    height: 100%;
    border: none;
    background: #409eff;
    outline: none;
    cursor: pointer;
  }
  .btn:active{
    background: #66b1ff;
  }
  .btn-a{
    background: #e4e7ed;
    cursor: not-allowed;
  }
</style>
