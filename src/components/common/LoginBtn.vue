<template>
  <div class="btnparent" @click="registerClick">
    <div class="loginbtn">{{btnText}}</div>
  </div>
</template>

<script>
export default {
    props:['btnText'],
    methods:{
      registerClick(){
        this.$emit('registeSubmit')
      }
    }
}
</script>

<style lang="less">
  .btnparent{
    padding:15px 10px;
  }
  .loginbtn{
    height:12.5vw;
    background-color:#ff9db5;
    color:white;
    display:flex;
    justify-content:center;
    align-items:center;
    border-radius:6.25vw;
    font-size:4.444vw;
  }
</style>
