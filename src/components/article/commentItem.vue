<!-- 二三级评论 -->
<template>
  <div class="commentitems" v-if="commentChild">
    <div class="commentItem" v-for="(item,index) in commentChild" :key="index">
        <div class="userImg">
          <img v-if="item.userinfo && item.userinfo.user_img" :src="item.userinfo.user_img" alt="">
          <img v-else src="@/assets/default_img.jpg" alt="">
          <p>
            <span v-if="item.userinfo">{{item.userinfo.name}}</span>
            <span v-else>此用户无姓名</span>
            <span>{{item.comment_date}}</span>
          </p>
        </div>
        <div class="commentContent">
          <!-- 二级评论 -->
          <div v-if="!temp">{{item.comment_content}}
            <span class="publish" @click="PostItemcomment(item.comment_id)">回复</span>
          </div>
          <div v-else>回复
            <span style="color:#478ef0;">{{item.parent_user_info.name}}</span>:
            {{item.comment_content}}
            <span class="publish" @click="PostItemcomment(item.comment_id)">回复</span>
          </div>
        </div>
        <!-- 三级评论后的递归 -->
          <commentchild-item :commentChild="item.child" @postChild="postChild" :temp="true"></commentchild-item>
      </div>
  </div>
</template>

<script>
export default {
    name:'commentchildItem',
    props:['commentChild','temp'],
    data() {
        return {

        }
    },
    components:{

    },
    methods:{
      PostItemcomment(id){
        this.$emit('postChild',id)
        this.$emit('PostPublish',id)
      },
      postChild(id){
        this.PostItemcomment(id)
        this.$emit('PostPublish',id)
      }
    }
}
</script>

<style lang="less">
  .commentitems{
    .commentItem{
      display:flex;
      flex-direction:column;
      .userImg{
        display:flex;
        img{
          margin:0 5px 10px 0;
        }
        p{
          flex:1;
          font-size:13px;
          color:#555;
          display:flex;
          justify-content:space-between;
          margin-bottom:5px;
        }
      }
      .commentContent{
        position:relative;
        margin-bottom:2.778vw;
        .publish{
          position:absolute;
          right:15px;
          color:red;
        }
      }
    }
  }
</style>
