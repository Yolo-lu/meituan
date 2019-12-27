<template>
  <div>
    <div class="head">
      <div class="left">
        <img src="../../assets/images/location.svg" alt class="icon" />
        <div>
          <span>{{location.city}}</span>
          <span class="changeCity">切换城市</span>
          <span>[新津县 崇州 彭州]</span>
          <span class="login">立即登录</span>
          <span @click="register">注册</span>
        </div>
      </div>
      <div class="right">
        <div class="item">
          <div class="one ones">我的美团</div>
          <div class="list">
            <div class="one">我的订单</div>
            <div class="one">我的收藏</div>
            <div class="one">抵用券</div>
            <div class="one">账户设置</div>
          </div>
        </div>
        <div class="items">
          <div class="one ones">美团app</div>
        </div>
        <div class="item">
          <div class="one ones">商家中心</div>
          <div class="list">
            <div class="one">美团餐饮商户中心</div>
            <div class="one">登录商家中心</div>
            <div class="one">美团智能收银</div>
            <div class="one">我想合作</div>
            <div class="one">手机免费开店</div>
            <div class="one">餐饮代理商招募</div>
            <div class="one">商家申请开票</div>
            <div class="one">免费合作美团排队</div>
          </div>
        </div>
        <div class="item">
          <div class="one ones">美团规则</div>
          <div class="list">
            <div class="one">规则中心</div>
            <div class="one">规则目录</div>
            <div class="one">规则评议院</div>
          </div>
        </div>
        <div class="lastItem">
          <div class="one ones">网站导航</div>
          <div class="lists">
            <div class="web">
              <div class="first">
                <div style="text-align:center">酒店旅游</div>
                <div class="bottom">
                  <div class="a">
                    <div class="one">国际机票</div>
                    <div class="one">经济型酒店</div>
                    <div class="one">公寓</div>
                    <div class="one">青年旅社</div>
                    <div class="one">农家院</div>
                  </div>
                  <div class="b" style="margin: 0 30px">
                    <div class="one">火车票</div>
                    <div class="one">主题酒店</div>
                    <div class="one">豪华酒店</div>
                    <div class="one">主题酒店</div>
                  </div>
                  <div class="c">
                    <div class="one">榛果民宿</div>
                    <div class="one">商务酒店</div>
                    <div class="one">客栈</div>
                    <div class="one">别墅</div>
                  </div>
                </div>
              </div>
              <div class="two">
                <div style="text-align:center">吃美食</div>
                <div class="bottom">
                  <div class="a">
                    <div class="one">烤鱼</div>
                    <div class="one">烧烤</div>
                    <div class="one">火锅</div>
                  </div>
                  <div class="b" style="margin: 0 30px">
                    <div class="one">特色小吃</div>
                    <div class="one">自助餐</div>
                    <div class="one">代金券</div>
                  </div>
                </div>
              </div>
              <div class="three">
                <div style="text-align:center">看电影</div>
                <div class="bottom">
                  <div class="a">
                    <div class="one">热映电影</div>
                    <div class="one">热门影院</div>
                    <div class="one">热映电影口碑榜</div>
                    <div class="one">最受期待电影</div>
                    <div class="one">国内票房榜</div>
                    <div class="one">北美票房榜</div>
                    <div class="one">电影票房榜</div>
                  </div>
                </div>
              </div>
              <div class="four">
                <div style="text-align:center">手机应用</div>
                <div class="bottom">
                  <img src="../../assets/images/meituan.png" alt />
                  <img src="../..//assets/images/waimai.png" alt />
                  <img src="../../assets/images/zhenguo.png" alt />
                  <img src="../../assets/images/dianping.png" alt />
                  <img src="../../assets/images/maoyan.png" alt />
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
      
<script>
export default {
  data() {
    return {};
  },
  components: {},
  methods: {
    register(){
      this.$router.push('/register')
    }
  },
  mounted() {},
  watch: {},
  computed: {
    location() {
      return this.$store.state.location;
    }
  }
};
</script>
      
<style scoped lang='scss'>
.head {
  display: flex;
  justify-content: space-between;
  margin-top: 10px;
}
.left {
  display: flex;
  .changeCity {
    background: #f4f4f4;
    padding: 2px;
  }
  .login {
    margin: 0 20px;
    color: #fe8c00;
  }
}
.right {
  display: flex;
  .items {
    padding: 0 14px;
  }
  .lastItem {
    padding: 0 14px;
    &:hover {
      .lists {
        display: block;
      }
    }
    .lists {
      display: none;
    }
  }
  .item {
    padding: 0 14px;
    &:hover {
      //  border:1px solid #e2e2e2;
      // //  box-shadow: 2px 2px 2px #e2e2e2;
      //  border-bottom: 0;
      //  border-top: 0;
      .list {
       padding: 0 10px;
        margin-left: -15px;
        display: block;
        position: absolute;
        z-index: 99;
        text-align: center;
       border:1px solid #e2e2e2;
       border-top: 0;
       background: #fff;
        // box-shadow: 2px 2px 2px #e2e2e2;
      }
    }

    .list {
      display: none;
    }
  }
}
.lists {
  .web {
    z-index: 99;
    border:1px solid #e2e2e2;
    padding: 30px 0;
    box-shadow: 2px 2px 2px #e2e2e2;
    position: absolute;
    left: 115px;
    right: 115px;
    min-width: 960px;
    max-width: 1120px;
    margin: auto;
    display: flex;
    justify-content: space-between;
    background: #fff;
    .bottom {
      padding-top: 35px;
      display: flex;
      justify-content: space-between;

      img {
        width: 60px;
        height: 60px;
        margin: 10px;
      }
      .a,
      .b,
      .c {
        color: #999;
        text-align: center;
      }
    }
  }
}
.ones {
  margin-top: 0 !important;
}
.one {
  margin: 10px 0;
  &:hover {
    color: #fe8c00;
  }
}

</style>