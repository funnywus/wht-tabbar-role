<script>
export default {
  data() {
    return {
      currentRole: '',
      roles: [
        { name: '用户' },
        { name: '商家' }
      ]
    }
  },
  
  created() {
    // 从本地存储获取当前角色
    try {
      const roleType = uni.getStorageSync('roleType')
      this.currentRole = roleType === 'provider' ? '商家' : '用户'
    } catch (e) {
      console.error('获取角色信息失败', e)
      this.currentRole = '用户' // 默认值
    }
  },
  
  methods: {
    goLogin() {
      uni.redirectTo({
        url: '/pages/login/login'
      })
    }
  }
}
</script>

<template>
  <view class="home-container">
    <view class="title">首页</view>
    
    <view class="current-role">
      当前身份：{{ currentRole }}
    </view>
    
    <button class="login-btn" @click="goLogin">返回登录</button>
  </view>
</template>

<style scoped lang="scss">
.home-container {
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  
  .title {
    font-size: 24px;
    font-weight: bold;
    margin-bottom: 30px;
    color: #333;
  }
  
  .current-role {
    font-size: 16px;
    color: #666;
    margin-bottom: 20px;
    padding: 10px 20px;
    background-color: #f5f5f5;
    border-radius: 8px;
  }
  
  .roles-container {
    display: flex;
    justify-content: space-around;
    width: 100%;
    margin-bottom: 40px;
    
    .role-item {
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 15px;
      
      .role-icon {
        width: 60px;
        height: 60px;
        margin-bottom: 10px;
      }
      
      .role-name {
        font-size: 16px;
        color: #333;
      }
    }
  }
  
  .login-btn {
    background-color: #007AFF;
    color: white;
    border: none;
    padding: 10px 30px;
    border-radius: 25px;
    font-size: 16px;
    
    &:active {
      background-color: #0056b3;
    }
  }
}
</style>
