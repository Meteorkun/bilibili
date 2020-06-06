<template>
  <div>
      <van-field
      :label="label"
      :type="type"
      :placeholder="placeholder"
      v-model="content"
      />
  </div>
</template>

<script>
export default {
  data(){
    return{
      content:'',
    }
  },
  methods:{
    handlerulg(){
      const rue = new RegExp(this.rule)
      if(rue.test(this.content)){
        this.$emit('inputChange',this.content)
      }
    }
  },
  props:['label','type','placeholder','rule'],
  watch:{
    content(){
      this.handlerulg()
    }
  }
}
</script>

<style lang="less">

</style>
