<template>
  <div class="main">
    <div class="login-container">
      <div class="left">
        <img
          src="http://www-wms-java.itheima.net/img/title.ef005a7a.png"
          alt=""
        >
        <el-form
          ref="ruleForm"
          :model="ruleForm"
          :rules="rules"
          label-width="100px"
          class="demo-ruleForm"
        >
          <el-form-item prop="username">
            <el-input v-model="ruleForm.username" type="input">
              <i slot="prefix" class="el-input__icon el-icon-mobile" />
            </el-input>
          </el-form-item>
          <el-form-item prop="password">
            <el-input v-model="ruleForm.password" type="password" show-password>
              <i slot="prefix" class="el-input__icon el-icon-lock" />
            </el-input>
          </el-form-item>
          <el-form-item>
            <el-checkbox
              v-model="checked"
              class="isChecked"
              @click="checked = !checked"
            >记住密码</el-checkbox></el-form-item>
        </el-form>
        <el-button class="btn" @click="goLogin">立即登录</el-button>
      </div>
      <div class="right" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      checked: false,
      ruleForm: {
        username: 'admin',
        password: 111111
      },
      rules: {
        username: [
          {
            required: true,
            message: '账号不能为空',
            trigger: 'blur'
          },
          {
            pattern: /^admin$/,
            message: '账号错误，请重新输入',
            trigger: 'blur'
          }
        ],
        password: [
          {
            required: true,
            message: '密码不能为空',
            trigger: 'blur'
          },
          {
            pattern: /^111111$/,
            message: '密码错误，请重新输入',
            trigger: 'blur'
          }
        ]
      }
    }
  },
  methods: {
    goLogin() {
      this.$loading = true
      this.$router.push('/')
      this.$loading = false
    }
  }
}
</script>

<style lang="scss" scoped>
.main {
  width: 100%;
  // position: relative;
  height: 100%;
}
.login-container {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  box-shadow: 5px 5px 5px 5px #ebebeb;
  margin: auto;
  display: flex;
  border-radius: 34px;
  width: 958px;
  height: 516px;
}
.left {
  width: 398px;
  height: 516px;
  border-radius: 34px 0 0 34px;
  margin: 0 auto;
  text-align: center;
  position: relative;
  img {
    width: 156px;
    height: 64px;
    margin-top: 70px;
  }

  i {
    margin-left: -5px;
    margin-top: 20px;
    font-size: 25px;
    width: 50px;
    height: 50px;
    background: #eae7e7;
    border-radius: 8px 0 0 8px;
  }
}
.right {
  background-image: url("http://www-wms-java.itheima.net/img/contentBg.1321d126.png");
  background-position: 50%;
  background-repeat: no-repeat;
  background-size: cover;
  width: 560px;
  height: 516px;
}
</style>

<style scoped lang="scss">
  ::v-deep .el-form-item__content {
    margin-left: 0;
  }
  ::v-deep .isChecked {
    margin-top: 10px;
    margin-left: -210px;
  }
  ::v-deep .el-checkbox__inner {
    border: 1px solid #ffb200;
  }
  ::v-deep .el-checkbox__input.is-checked .el-checkbox__inner,
  .el-checkbox__input.is-indeterminate .el-checkbox__inner {
    background-color: #ffb200;
    border-color: #ffb200;
  }
  ::v-deep .el-checkbox__input.is-checked + .el-checkbox__label {
    color: #ffb200;
  }
  ::v-deep .btn {
    margin-top: 266px;
    width: 290px;
    height: 50px;
    background: #ffb200;
    border-radius: 8px;
    box-shadow: 0 2px 9px 1px rgb(255 178 0 / 47%);
    font-size: 16px;
    font-weight: 600;
    text-align: center;
    color: #332929;
    line-height: 22px;
  }
   ::v-deep .el-form {
    position: absolute;
    top: 52%;
    left: 38%;
    transform: translate(-50%, -50%);
    // margin: 0 auto;
    width: 400px;
  }
  ::v-deep .el-input__inner {
    background-color: #f8f5f5;
    height: 50px;
    padding-top: 4px;
    border-radius: 8px;
    margin-top: 20px;
    padding-left: 59px;
  }
</style>
