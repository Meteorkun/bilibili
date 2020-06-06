<template>
  <div class="userdetail">
    <div>
      <div class="user_img">
        <img :src="userinfo.user_img" alt="" v-if="userinfo.user_img">
        <img src="@/assets/default_img.jpg" alt v-else />
      </div>
      <div class="user_edit">
        <div>
          <p>
            <span>0</span>
            <span class="user_text">粉丝</span>
          </p>
          <p>
            <span>54</span>
            <span class="user_text">关注</span>
          </p>
          <p>
            <span>0</span>
            <span class="user_text">获赞</span>
          </p>
        </div>
        <div @click="$router.push('/edit')">
          <div class="user_editBtn">编辑资料</div>
        </div>
      </div>
    </div>
    <div>
      <h2>{{userinfo.username}}</h2>
      <p>{{userinfo.user_desc}}</p>
    </div>
  </div>
</template>

<script>
export default {
  props:['userinfo'],
  data(){
    return{
      model:{}
    }
  }
};
</script>

<style scoped lang="less">
.userdetail {
  background-color: white;
  padding:0 3.333vw;
  >div:nth-child(1){
      display:flex;
      .user_img{
        margin-right: 20px;
        img{
          width: 85px;
          height: 85px;
          border-radius: 50%;
        }
      }
      .user_edit{
      flex:1;
      div:nth-child(1){
        display:flex;
        padding:10px;
        p{
          flex:1;
          display:flex;
          justify-content:center;
          align-items:center;
          flex-direction: column;
          font-size: 13px;
          .user_text{
            color:#aaa;
          }
        }
        p:nth-child(1),p:nth-child(2){
          border-right:1px solid #ccc;
        }
      }
        div:nth-child(2){
          padding:12px 10px;
          .user_editBtn {
            border: 1px solid #fb7a9f;
            padding: 3px;
            color: #fb7a9f;
            display:flex;
            justify-content:center;
            align-items:center;
            border-radius: 3px;
          }
        }
      }
  }
  div:nth-child(2){
    h2{
      margin:10px 0 3px 0;
      font-weight: 400;
    }
    p{
      margin:10px 0;
      padding:0;
      color: #555;
    }
  }
}
</style>
