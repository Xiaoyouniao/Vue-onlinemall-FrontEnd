<template>
  <div>
    <header class="header">
      <symbol id="icon-cart" viewBox="0 0 38 32">
        <title>cart</title>
        <path class="path1" d="M37.759 0h-4.133c-0.733 0.004-1.337 0.549-1.434 1.255l-0.546 4.342c-0.081 0.484-0.496 0.849-0.997 0.849-0.005 0-0.009-0-0.014-0h-27.604c-0.003 0-0.007-0-0.011-0-1.674 0-3.031 1.357-3.031 3.031 0 0.34 0.056 0.666 0.159 0.971l2.52 8.062c0.385 1.194 1.486 2.043 2.785 2.043 0.126 0 0.25-0.008 0.372-0.023l22.983 0.002c0.515 0.131 0.626 0.768 0.626 1.283 0.005 0.044 0.009 0.095 0.009 0.146 0 0.501-0.294 0.933-0.718 1.134l-22.439 0.003c-0.354 0-0.642 0.287-0.642 0.642s0.287 0.642 0.642 0.642h22.745l0.131-0.071c0.919-0.392 1.551-1.287 1.551-2.33 0-0.058-0.002-0.116-0.006-0.173 0.021-0.108 0.033-0.24 0.033-0.376 0-1.072-0.732-1.973-1.724-2.23l-23.357-0.004c-0.063 0.008-0.135 0.013-0.209 0.013-0.719 0-1.332-0.455-1.566-1.093l-2.53-8.095c-0.048-0.154-0.076-0.332-0.076-0.515 0-0.973 0.782-1.764 1.752-1.778h27.657c1.159-0.004 2.112-0.883 2.232-2.011l0.547-4.345c0.010-0.083 0.078-0.147 0.161-0.152l4.133-0c0.354 0 0.642-0.287 0.642-0.642s-0.287-0.642-0.642-0.642z"></path>
        <path class="path2" d="M31.323 9.69c-0.022-0.003-0.048-0.004-0.074-0.004-0.328 0-0.598 0.248-0.633 0.567l-0.809 7.268c-0.003 0.022-0.004 0.048-0.004 0.074 0 0.328 0.248 0.598 0.567 0.633l0.074 0c0.001 0 0.003 0 0.004 0 0.327 0 0.596-0.246 0.632-0.563l0.809-7.268c0.003-0.022 0.004-0.048 0.004-0.074 0-0.328-0.248-0.598-0.567-0.633z"></path>
        <path class="path3" d="M27.514 25.594c-1.769 0-3.203 1.434-3.203 3.203s1.434 3.203 3.203 3.203c1.769 0 3.203-1.434 3.203-3.203s-1.434-3.203-3.203-3.203zM27.514 30.717c-1.060 0-1.92-0.86-1.92-1.92s0.86-1.92 1.92-1.92c1.060 0 1.92 0.86 1.92 1.92s-0.86 1.92-1.92 1.92z"></path>
        <path class="path4" d="M9.599 25.594c-1.769 0-3.203 1.434-3.203 3.203s1.434 3.203 3.203 3.203c1.769 0 3.203-1.434 3.203-3.203s-1.434-3.203-3.203-3.203zM9.599 30.717c-1.060 0-1.92-0.86-1.92-1.92s0.86-1.92 1.92-1.92c1.060 0 1.92 0.86 1.92 1.92s-0.86 1.92-1.92 1.92z"></path>
      </symbol>
      <div class="navbar">
        <div class="navbar-left-container">
            <h2 class="navbar-brand-logo">阳光商城</h2>
        </div>
        <div class="navbar-right-container" style="display: flex;">
          <div class="navbar-menu-container">
            <!--<a href="/" class="navbar-link">我的账户</a>-->
            <span class="navbar-link" v-show='loginTagFlag'>{{ userName }}</span>
            <a href="javascript:void(0)" class="navbar-link" @click="userName='';userPwd='';loginModalFlag=true" v-show='!loginTagFlag'>Login</a>
            <a href="javascript:void(0)" class="navbar-link" @click="logout" v-show='loginTagFlag'>Logout</a>
            <div class="navbar-cart-container" @click="showCartModal">
              <span class="navbar-cart-count" v-show="userName">{{ cartCount }}</span>
              <a class="navbar-link navbar-cart-link">
                <svg class="navbar-cart-logo">
                  <use xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="../../static/svg.svg#icon-cart"></use>
                </svg>
              </a>
            </div>
          </div>
        </div>
      </div>
      <div class="md-modal modal-msg md-modal-transition" v-bind:class="{'md-show':loginModalFlag}">
          <div class="md-modal-inner">
            <div class="md-top">
              <div class="md-title">Login in</div>
              <button class="md-close" @click="loginModalFlag=false">Close</button>
            </div>
            <div class="md-content">
              <div class="confirm-tips">
                <div class="error-wrap">
                  <span class="error error-show" v-text="errorTip" v-show="errorTip"></span>
                </div>
                <ul>
                  <li class="regi_form_input">
                    <i class="icon IconPeople"></i>
                    <input type="text" tabindex="1" name="loginname" v-model="userName" class="regi_login_input regi_login_input_left" placeholder="User Name" data-type="loginname">
                  </li>
                  <li class="regi_form_input noMargin">
                    <i class="icon IconPwd"></i>
                    <input type="password" tabindex="2"  name="password" v-model="userPwd" class="regi_login_input regi_login_input_left login-input-no input_text" placeholder="Password" @keyup.enter="login">
                  </li>
                </ul>
              </div>
              <div class="login-wrap">
                <a href="javascript:;" class="btn-login" @click="login">登  录</a>
              </div>
            </div>
          </div>
        </div>
      <div class="md-overlay" v-if="loginModalFlag" @click="loginModalFlag=false"></div>
      <div class="md-modal modal-msg md-modal-transition" v-bind:class="{'md-show':cartModalFlag}">
          <div class="md-modal-inner">
            <div class="md-top">
              <button class="md-close" @click="cartModalFlag=false">Close</button>
            </div>
            <div class="md-content">
              <div class="confirm-tips">
                <h3>您尚未登录，请登录后再查看购物车</h3>
              </div>
              <div class="btn-wrap">
                <a href="javascript:;" class="btn btn--m" @click="cartModalFlag=false">确定</a>
              </div>
            </div>
          </div>
        </div>
      <div class="md-overlay" v-if="cartModalFlag" @click="cartModalFlag=false"></div>
    </header>
  </div>
</template>

<style>
  .header {
    width: 100%;
    background-color: white;
    font-family: "moderat",sans-serif;
    font-size: 16px;
  }
  .navbar {
    display: flex;
    justify-content: space-between;
    align-content: center;
    width: 100%;
    height: 70px;
    max-width: 1280px;
    margin: 0 auto;
    padding: 5px 20px 10px 20px;
  }
  .navbar-left-container {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    margin-left: -20px;
  }
  .navbar-brand-logo {
    letter-spacing: 0.25em;
    font-size: 30px;
    font-weight: bold;
    text-indent: 10px;
    font-family: '黑体';
  }
  .header a, .footer a {
    color: #666;
    text-decoration: none;
  }
  a {
    -webkit-transition: color .3s ease-out;
    transition: color .3s ease-out;
  }
  .navbar-right-container {
    display: none;
    justify-content: flex-start;
    align-items: center;
  }
  .navbar-menu-container {
    display: flex;
    justify-content: flex-end;
    align-items: center;
    padding-top: 10px;
  }
  .navbar-link {
    padding-left: 15px;
  }
  .navbar-cart-container {
    position: relative;
  }
  .navbar-cart-count {
    justify-content: center;
    align-items: center;
    position: absolute;
    top: -9px;
    right: -11px;
    width: 20px;
    border-radius: 10px;
    color: white;
    background-color: #eb767d;
    font-size: 16px;
    font-weight: bold;
    text-align: center;
  }
  .navbar-cart-logo {
    width: 25px;
    height: 25px;
    transform: scaleX(-1);
  }
</style>

<script>
import '../assets/css/login.css'
import axios from 'axios'

export default {
  data(){
    return{
      loginTagFlag: false, //控制登录栏login/logout两标签的显示
      checkLoginFlag: false, //打开页面后检查是否已经登录的数据
      loginModalFlag: false, //控制登录模态框是否显示
      cartModalFlag: false, //控制购物车模态框是否显示
      userName:'',//用户名，用于提交和显示
      userPwd: '',//用户密码，用于提交给数据库
      errorTip: '', // 表单提交错误提示
      cartCount: 0
    }
  }, 
  props: ["num"],
  mounted(){
    this.checkLogin() 
  },
  methods:{
    checkLogin(){ //页面加载后校验是否已登录
      axios.get('users/checkLogin').then(res=>{
        if(res.data.status==1){
          this.checkLoginFlag=false
        }else{
          this.userName = res.data.result
          this.loginTagFlag = true
          
          axios.get('users/getCartCount').then(res=>{
            this.cartCount = res.data.result
          })
        }
      })
    },
    login(){ // 点击login按钮后处理登录逻辑
    /**
     * 1.获取表单提交内容
     * 2.校验表单提交内容
     * 3.将提交数据发往数据库，根据响应结果作出不同反应，并给出错误提示
     */

      if(!this.userName || !this.userPwd) {
        return this.errorTip = '请输入用户名和密码'
      }
      axios.post('users/login',{userName:this.userName,userPwd:this.userPwd}).then(res=>{
        if(res.data.status == 0) {
          this.loginModalFlag = false
          this.userName = res.data.result.userName
          this.loginTagFlag = true
          this.imlogined()
        } else {
          this.errorTip = res.data.msg
        }
      })
    },
    logout(){ // 点击logout按钮退出登录
    /**
     * 1.向服务器发送请求，退出登录
     * 2.隐藏用户名和logout按钮，显示login按钮
     */
      axios.post('users/logout').then(res=>{
        if(res.data.status==0){
          this.userName= ''
          this.loginTagFlag=false
          this.imlogined()
        }
      })
    },
    showCartModal(){ //点击购物车按钮
      /**
       * 1. 判断登录情况，根据登录情况做不同处理
       * 2. 未登录，确认
       * 3. 已登录，页面跳转
       */
      
      if(!document.cookie) { 
        this.cartModalFlag = true  
      } else {
        this.$router.push({path: '/cart'}); 
      }
    },
    imlogined(){
      this.$emit('rylogined',{ userName: this.userName })
    }
  }
}
  
</script>