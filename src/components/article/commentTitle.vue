<template>
  <div class="comment">
    <p class="comment-title">
      <span>评论</span>
      <span>{{dataLength}}</span>
    </p>
    <div class="commentMyinfo">
      <img :src="myuser.user_img" alt="" v-if="myuser">
      <img src="@/assets/default_img.jpg" alt="" v-else>
      <input type="text" placeholder="说点什么吧" v-model="commentcontent" ref="Postipt">
      <button @click="cmmentPublish">发表</button>
    </div>
  </div>
</template>

<script>
export default {
    props:['dataLength'],
    data() {
        return {
          myuser:null,
          commentcontent:''
        }
    },
    components:{

    },
    methods:{
      async myUserinfo(){
        const res = await this.$http.get('/user/' +localStorage.getItem('id'))
        this.myuser = res.data[0]
      },
      cmmentPublish(){
        if(!this.myuser && !localStorage.getItem('token')&& !localStorage.getItem('id')){
          this.$msg.fail('请先登录')
          return
        }
        this.$emit('Postcomment',this.commentcontent)
        this.commentcontent = ''
      },
      focusipt(){
        this.$refs.Postipt.focus()
      }
    },
    created(){
      if(localStorage.getItem('token')){
            this.myUserinfo();
      }
    }
}
</script>

<style lang="less">
  .comment{
    padding:8.333vw 2.778vw 0 2.778vw;
    .comment-title{
      span:nth-child(2){
        margin-left:2.778vw;
        color:#aaa;
      }
    }
    .commentMyinfo{
      padding:2.778vw 0;
      display:flex;
      img{
        height:7.994vw;
        width:7.994vw;
        border-radius:50%;
      }
      input{
        outline:none;
        border:0;
        background-color:#f4f4f4;
        border-radius:13px;
        font-size:12px;
        padding:0 20px 0 15px;
        margin-left:10px;
      }
      button{
        outline:none;
        border:0;
        border-radius:12px;
        background:#fb7299;
        color:white;
        padding:0 15px;
      }
    }
  }
</style>
