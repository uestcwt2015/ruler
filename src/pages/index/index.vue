<template>
  <div class="container">
    <div class="userinfo">
      <open-data class="userinfo-avatar" type="userAvatarUrl"></open-data>
      <open-data type="userNickName"></open-data>
    </div>

    <Button text="开始使用" to="calc"></Button>
  </div>
</template>

<script>
import Button from '@/components/button.vue';

export default {
  data () {
    return {
      motto: 'Hello World',
      userInfo: {}
    }
  },

  components: {
    Button
  },

  methods: {
    // bindViewTap () {
    //   const url = '../calc/main'
    //   wx.navigateTo({ url })
    // },
    // getUserInfo () {
    //   // 调用登录接口
    //   wx.login({
    //     success: () => {
    //       wx.getUserInfo({
    //         success: (res) => {
    //           this.userInfo = res.userInfo
    //           console.log(res.userInfo);
    //         }
    //       })
    //     }
    //   })
    // }
  },
  created () {
    // 调用应用实例的方法获取全局数据
    // this.getUserInfo()
  }
}
</script>

<style>
.userinfo {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.userinfo-avatar {
  width: 200rpx;
  height: 200rpx;
  margin: 20rpx;
  border-radius: 50%;
}

.userinfo-nickname {
  color: #aaa;
}

.button {
  margin-top: 40vh;
}
</style>
