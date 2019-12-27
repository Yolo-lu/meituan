<template>
  <div>
    <div class="wrap">
      <div class="head">
        <div class="left">
          <img src="../../assets/images/logo.png" alt />
        </div>
        <div class="right">
          <div class="text">已有美团账号？</div>
          <div class="login">登录</div>
        </div>
      </div>
    </div>
    <div style="border-top:1px solid #e2e2e2;">
      <Form ref="formValidate" :model="formValidate" :rules="ruleValidate" :label-width="80">
        <div class="inputs">
          <FormItem label="昵称" prop="name">
            <Input v-model="formValidate.name"></Input>
          </FormItem>
        </div>
        <div class="inputs">
          <FormItem label="手机" prop="phone">
            <Input v-model="formValidate.phone"></Input>
          </FormItem>
        </div>
        <div class="inputs">
          <span>
            <FormItem label="验证码" prop="code">
              <Input v-model="formValidate.code"></Input>
            </FormItem>
          </span>
          <span class="Code">
            <Button size="small">发送验证码</Button>
          </span>
        </div>
        <div class="inputs">
          <FormItem label="密码" prop="password">
            <Input type="password" v-model="formValidate.password"></Input>
          </FormItem>
        </div>
        <div class="inputs">
          <FormItem label="确认密码" prop="repassword">
            <Input type="password" v-model="formValidate.repassword"></Input>
          </FormItem>
        </div>
      </Form>
      <div class="bottom">
          <div class="agreen">同意以下协议并注册</div>
          <div style="display:flex;color: #FE8C00;margin-top:10px">
              <div>《美团点评用户服务协议》</div>
          <div>《美团点评隐私政策》</div>
          </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    const validatePass = (rule, value, callback) => {
      if (value === "") {
        callback(new Error("Please enter your password"));
      } else {
        if (this.formValidate.repassword !== "") {
          // 对第二个密码框单独验证
          this.$refs.formCustom.validateField("repassword");
        }
        callback();
      }
    };
    const validatePassCheck = (rule, value, callback) => {
      if (value === "") {
        callback(new Error("Please enter your password again"));
      } else if (value !== this.formValidate.password) {
        callback(new Error("The two input passwords do not match!"));
      } else {
        callback();
      }
    };
    return {
      formValidate: {
        name: "",
        phone: "",
        code: "",
        password: "",
        repassword: ""
      },

      ruleValidate: {
        name: [
          {
            required: true,
            message: "The name cannot be empty",
            trigger: "blur"
          }
        ],
        phone: [
          {
            required: true,
            message: "The phone cannot be empty",
            trigger: "blur"
          }
        ],
        code: [
          {
            required: true,
            message: "The code cannot be empty",
            trigger: "blur"
          }
        ],
        password: [{ validator: validatePass, trigger: "blur", required: true }],
        repassword: [
          { validator: validatePassCheck, trigger: "blur", required: true }
        ]
      }
    };
  },
  components: {},
  methods: {},
  mounted() {},
  watch: {},
  computed: {}
};
</script>

<style scoped lang='scss'>
.head {
  padding: 10px 30px;
  height: 60px;
  display: flex;
  justify-content: space-between;
  .left img {
    width: 120px;
    height: 36px;
  }
  .right {
    display: flex;
    .text {
      font-size: 14px;
      color: #333;
      line-height: 36px;
      margin-right: 10px;
    }
    .login {
      background: #ffc300;
      padding: 3px 10px;
      line-height: 36px;
      border-radius: 10px;
    }
  }
}
.inputs {
  width: 20%;
  margin: 30px 0 20px 200px;
  .Code {
    position: relative;
    left: 80px;
    top: -10px;
  }
}
.bottom{
    margin: 30px 0 20px 280px;
}
.agreen{
     background: #ffc300;
      padding: 3px 10px;
      line-height: 36px;
      border-radius: 10px;
      width: 140px
}
</style>