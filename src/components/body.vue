<template>
  <div class="body">
    <img src="../assets/bg1.png" alt="" class="imgPostion" />
    <img src="../assets/bg2.png" alt="" class="imgPostionBootom" />
    <div class="contation">
      <div class="section">
        <div class="section-left">
          <div class="section-left-imgBox">
            <img
              src="https://gitee.com/static/images/logo.svg?t=158106664"
              alt=""
            />
            <h2>企业级 DevOps 研发管理平台</h2>
          </div>
          <div class="section-left-center">
            <div>
              <span class="name">{{ name }}</span>
              <span class="name" style="margin-left: 12px">{{ title }}</span>
            </div>
            <div style="margin-top: 16px; line-height: 1.7">
              {{ content }}
            </div>
          </div>
          <div class="section-left-footer">
            <strong class="section-left-booterHot">Gitee 企业版</strong>
            <span style="margin: 0 10px"
              ><img src="../assets/hot.png" alt="" width="25"
            /></span>
            <span>企业级 DevOps 研发管理平台</span>
            <img src="../assets/jiantou.png" alt="" width="13" />
          </div>
        </div>
        <div class="section-right">
          <div class="section-right-header">
            <h2>
              <span>{{ LoginShow ? '登录' : '注册' }}</span>
            </h2>
            <div class="section-right-header-denglu">
              <span>{{ LoginShow ? '没有账号？' : '已有账号' }} </span>
              <span
                style="color: #5a94ad; margin-left: 5px; cursor: pointer"
                @click="LoginShow = !LoginShow"
                >{{ LoginShow ? '点此注册' : '点此登录' }}</span
              >
            </div>
          </div>
          <div>
            <el-form
              v-if="LoginShow"
              :model="ruleForm"
              :rules="rules"
              ref="ruleForm"
              class="demo-ruleForm"
            >
              <el-form-item label="" prop="name" style="margin-bottom: 30px">
                <el-input
                  v-model="ruleForm.name"
                  placeholder="手机/邮箱/个人空间地址"
                ></el-input>
              </el-form-item>
              <el-form-item label="">
                <el-input
                  v-model="ruleForm.passWord"
                  type="password"
                  placeholder="请输入密码"
                ></el-input>
              </el-form-item>
            </el-form>
            <el-form
              v-else
              :model="registerForm"
              :rules="registerFormRules"
              ref="registerForm"
              class="demo-ruleForm"
            >
              <el-form-item label="" prop="name">
                <el-input
                  v-model="registerForm.name"
                  placeholder="姓名"
                ></el-input>
              </el-form-item>
              <el-form-item label="" prop="aadress">
                <el-input
                  placeholder="个人空间地址"
                  v-model="registerForm.aadress"
                >
                  <template slot="prepend">https://gitee.com/</template>
                </el-input>
              </el-form-item>
              <el-form-item label="" prop="phone">
                <el-input
                  v-model="registerForm.phone"
                  placeholder="请输入手机号码"
                ></el-input>
              </el-form-item>
              <el-form-item label="" prop="passWord">
                <el-input
                  v-model="registerForm.passWord"
                  type="password"
                  placeholder="密码不少于6位"
                ></el-input>
              </el-form-item>
            </el-form>
            <div
              style="display: flex; justify-content: space-between"
              v-if="LoginShow"
            >
              <el-checkbox v-model="checked">记住我</el-checkbox>
              <span style="color: #77a6bb">短信验证登录</span>
            </div>
            <div
              style="
                display: flex;
                justify-content: space-between;
                font-size: 14px;
              "
              v-else
            >
              <el-checkbox v-model="checked"></el-checkbox>
              <span style="color: black; margin-left: 5px">我已阅读并同意</span>
              <span style="color: #77a6bb">使用条款</span
              ><span style="color: black">及</span>
              <span style="color: #77a6bb">非活跃账号处理规范</span>
            </div>
            <div>
              <el-button class="denglu" v-if="LoginShow">登录</el-button>
              <el-button class="denglu" v-else>立即注册</el-button>
              <div
                v-if="LoginShow"
                style="
                  color: #1283ba;
                  text-align: center;
                  margin-top: 20px;
                  font-size: 14px;
                "
              >
                已有账号,忘记密码?
              </div>
            </div>
            <div class="right-c">
              <img src="../assets/c.png" alt="" />
              <span> 使用 OSChina 帐号登录</span>
            </div>
            <div class="right-bottom">
              <div class="other">
                <img src="../assets/line1.png" alt="" />
                <span style="color: #8c92a4; font-size: 14px"
                  >其他方式登录</span
                >
                <img src="../assets/line1.png" alt="" />
              </div>
            </div>
            <div class="right-bottom-icon">
              <img src="../assets/bottom1.png" alt="" />
              <img src="../assets/bottom2.png" alt="" />
              <img src="../assets/bottom3.png" alt="" />
              <img src="../assets/bottom4.png" alt="" />
              <img src="../assets/bottom5.png" alt="" />
            </div>
          </div>
        </div>
      </div>
      <div style="text-align: right">
        <img src="../assets/kefu.png" alt="" width="40" height="40" />
      </div>
      <div class="section-Footer">
        <span>© Gitee.com</span>
        <span>关于我们</span>
        <span>使用条款</span>
        <span>帮助文档</span>
        <span>在线自助服务</span>
        <span>重发激活邮件</span>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      dataList: [
        {
          name: '韩卿',
          title: 'Apache Kylin',
          content:
            '与其说喜欢 Gitee，其实更喜欢 Gitee的团队。红薯是我见过的最幽默而执着的程序员，认真做产品，有耐心不功利，所以我相信Gitee 一定会做的很好。',
        },
        {
          name: '阮一峰',
          title: '知名技术博主',
          content:
            'Gitee 是国内代码托管服务的领先者，很认真的产品。适合国内程序员习惯，访问速度极快。',
        },
        {
          name: '王安',
          title: 'DCloud CEO',
          content:
            '不少国内的好产品，因为用户的迷外心理而不被重视。其实一个友好的中文界面，可以让用户快速掌握软件的所有功能，实实在在地提升效率。期待更多开发者能重视 Gitee，重视国内认真做事的产品团队，他们会给你惊喜。',
        },
        {
          name: '贤心',
          title: 'layui',
          content:
            'Gitee 已成为我工作的依赖，从个人私有库到企业版，每一项解决方案都直击痛点。而它更吸引人的，是开放的姿态和优质的本土化基因。告诉世界：我们在自豪地使用 Gitee！',
        },
        {
          name: '熊平',
          title: '51CTO创始人',
          content:
            '与其说喜欢 Gitee，其实更喜欢 Gitee 的团队。红薯是我见过的最幽默而执着的程序员，认真做产品，有耐心不功利，所以我相信 Gitee 一定会做的很好',
        },
      ],
      LoginShow: true,
      checked: false,
      ruleForm: {
        name: '',
        passWord: '',
        aadress: '',
      },
      registerForm: {
        name: '',
        passWord: '',
        aadress: '',
        phone: '',
      },
      name: '',
      content: '',
      title: '',
      rules: {
        name: [{ required: true, message: '用户名为必填项', trigger: 'blur' }],
      },
      registerFormRules: {
        name: [{ required: true, message: '姓名为必填项', trigger: 'blur' }],
        aadress: [
          { required: true, message: '个人空间地址为必填项', trigger: 'blur' },
        ],
        phone: [{ required: true, message: '手机号为必填项', trigger: 'blur' }],
        passWord: [
          { required: true, message: '密码为必填项', trigger: 'blur' },
        ],
      },
    };
  },
  created() {
    this.content = this.dataList[Math.floor(Math.random() * 4) + 1].content;
    this.title = this.dataList[Math.floor(Math.random() * 4) + 1].title;
    this.name = this.dataList[Math.floor(Math.random() * 4) + 1].name;
  },
  methods: {},
};
</script>
<style>
.el-checkbox__input.is-checked + .el-checkbox__label {
  color: black !important;
}
.el-checkbox__input.is-checked .el-checkbox__inner {
  border: #fe7300 !important;
  background-color: #fe7300 !important;
}
.el-form-item.is-error .el-input__inner,
.el-form-item.is-error .el-input__inner:focus,
.el-form-item.is-error .el-textarea__inner,
.el-form-item.is-error .el-textarea__inner:focus,
.el-message-box__input input.invalid,
.el-message-box__input input.invalid:focus {
  border-left: 2px solid red;
  background-color: #fff0f0;
}
</style>
<style scoped lang="less">
.right-bottom {
  margin-top: 24px;
  text-align: center;
  width: 100%;
  .other {
    widows: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    span {
      margin: 0 20px;
    }
    img {
      width: 110px;
      // width: 20%;
    }
  }
  &-icon {
    margin-top: 10px;
    display: flex;
    justify-content: space-between;
    img {
      width: 32px;
      height: 32px;
    }
  }
}
::v-deep .el-button {
  margin-top: 20px;
  width: 100%;
  color: #fff;
  font-size: 18px;
  line-height: 22px;
  padding: 8px 26px;
  font-weight: 500;
  background-color: #f68521 !important;
}
.right-c {
  color: black;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 40px;
  img {
    width: 32px;
    height: 32px;
  }
  span {
    margin-left: 10px;
    font-size: 15px;
  }
}
.imgPostion {
  width: 394px;
  height: 468px;
  left: 0;
  content: '';
  position: fixed;
  bottom: 0;
  background-size: contain;
  background-repeat: no-repeat;
  z-index: -1;
}
.imgPostionBootom {
  content: '';
  position: fixed;
  bottom: 0;
  background-size: contain;
  background-repeat: no-repeat;
  z-index: -2;
  width: 487px;
  height: 412px;
  right: 0;
}
.body {
  width: 100%;
  height: 97vh;
  position: relative;

  .contation {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 1000px;
    padding: 0;
    transform: translate(-50%, -50%);
    .section {
      display: flex;
      margin-bottom: 10px;
      box-shadow: 0px 20px 80px 0px rgba(0, 0, 0, 0.3);
      .section-left {
        position: relative;
        width: 500px;
        color: #fff;
        padding: 80px 80px 48px;
        background: linear-gradient(0deg, #3a485a 0%, #607089 100%);
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        ::before {
          content: '';
          position: absolute;
          top: 0;
          left: 0;
          bottom: 0;
          right: 0;
          opacity: 0.3;
          background: url(../assets/left1.png) no-repeat 0 0;
        }
        ::after {
          content: '';
          position: absolute;
          top: 0;
          left: 0;
          bottom: 0;
          right: 0;
          opacity: 0.3;
          background: url(../assets/left2.png) no-repeat right bottom;
        }
        &-imgBox {
          img {
            width: 144px;
          }
        }
        &-center {
          flex: 1;
          margin-top: 46px;
          font-size: 14px;
          margin-bottom: 70px;
          .name {
            color: 14px;
            opacity: 0.5;
            color: #fff;
          }
        }
        .section-left-footer {
          font-size: 14px;
          padding-top: 40px;
          margin-top: 24px;
          border-top: 1px solid rgba(255, 255, 255, 0.2);
          .section-left-booterHot {
            ::after {
              content: 'hot';
              position: absolute;
              font-size: 12px;
              padding: 2px 6px;
              border-radius: 1px;
              margin-top: -12px;
              background-color: #c71d23;
              transform: scale(0.84);
            }
          }
        }
      }
      .section-right {
        width: 500px;
        color: #fff;
        background: #ffffff;
        padding: 64px 70px 48px;
        &-header {
          display: flex;
          margin-bottom: 4px;
          justify-content: space-between;
          align-items: center;
          color: black;
          &-denglu {
            font-size: 14px;
          }
        }
      }
    }
    .section-Footer {
      margin-top: 15px;
      text-align: center;
      z-index: -2;
      span {
        margin-left: 8px;
        color: #aeb2bf;
        font-size: 14px;
      }
    }
  }
}
</style>
