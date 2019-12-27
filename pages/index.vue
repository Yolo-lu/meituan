<template>
  <div>
    <div class="line">
      <div class="wrap">
        <div class="head">
          <div class="all">全部分类</div>
          <div v-for="(item,index) in list" :key="index" class="h-all">
            <div>{{item}}</div>
          </div>
        </div>
      </div>
    </div>
    <div class="wrap w-all">
      <div class="left">
        <div v-for="(item,index) in menu" :key="index">
          <div class="list">
            <div class="left1">
              <i class="iconfont" :class="icons[index].icon" :style="{color:icons[index].color}"></i>
              <div class="name">{{item.name}}</div>
              <div class="hot" v-if="index===2">HOT</div>
            </div>
            <div class="arrow-forward">
              <Icon type="ios-arrow-forward" />
            </div>
            <div class="lists">
              <div class="wraps" v-for="(item1,index1) in menu[index].child" :key="index1">
                <div class="head">
                  <div class="names">{{item1.title}}</div>
                  <div>
                    <span>更多</span>
                    <span>
                      <Icon type="ios-arrow-forward" />
                    </span>
                  </div>
                </div>
                <div class="item">
                  <div v-for="(item2,index2) in item1.child" :key="index2" class="items">{{item2}}</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="center">
        <div class="top">
          <div class="banner">
            <div style="width:550px">
              <Carousel v-model="value1" loop autoplay class="banner-list-width">
                <CarouselItem v-for="(item,index) in banner" :key="index">
                  <div class="demo-carousel">
                    <img :src="item.img" alt class="img" />
                  </div>
                </CarouselItem>
              </Carousel>
            </div>
          </div>
          <div class="c-r">
            <div style="width:150px">
              <img
                src="http://p0.meituan.net/codeman/e473bb428f070321269b23370ff02ba956209.jpg"
                alt
              />
            </div>
          </div>
          <div class="c-third">
            <div style="margin:auto">
              <div class="avatar">
                <img src="//s0.meituan.net/bs/fe-web-meituan/2d05c2b/img/avatar.jpg" alt />
              </div>
              <div class="hi">hi,你好</div>
              <div class="register">注册</div>
              <div class="register">立即登录</div>
            </div>
          </div>
        </div>
        <div class="bottom">
          <div class="b-two">
            <div class="b-img">
              <div class="bb-img">
                <img
                  src="http://p0.meituan.net/codeman/843d7347cb20d945e4bc39b6403f0515182965.png"
                  alt
                />
              </div>
              <div class="bb-img">
                <img
                  src="http://p1.meituan.net/codeman/16442c19da1f1c4544f794e29d99c92051716.jpg"
                  alt
                />
              </div>
            </div>
          </div>
          <div class="b-r">
            <div style="width:150px">
              <img
                src="http://p1.meituan.net/codeman/5b21cddb4bb1cbc3a9c3bce0f726c75940469.jpg"
                alt
              />
            </div>
          </div>
          <div class="c-b-third">
            <div class="erweima">
              <img src="//s1.meituan.net/bs/fe-web-meituan/60ac9a0/img/download-qr.png" alt />
            </div>
            <div class="phone">美团app手机版</div>
            <div style="text-align:center">
              <span class="red">1元起</span>
              <span style="color: #3f3f3f;">吃喝玩乐</span>
            </div>
          </div>
        </div>
      </div>
    </div>
     <div class="wrap">
      <tone></tone>
    </div>
  </div>
</template>

<script>
import tone from '../components/tone/index'
import { all } from "q";
export default {
  layout: "structrue",
  data() {
    return {
      location: {},
      menu: [], //分类
      banner: [], //轮播
      value1: 0,
      list: [
        "美团外卖",
        "猫眼电影",
        "美团酒店",
        "民宿／公寓",
        "商家入驻",
        "美团公益"
      ],
      icons: [
        { icon: "iconfood", color: "#ff8200" },
        { icon: "iconwaimai", color: "#ffb500" },
        { icon: "iconHotel", color: "#9B5E3E" },
        { icon: "iconzhenguo", color: "#ffb500" },
        { icon: "iconArtboard", color: "#ff3d00" },
        { icon: "iconjiaotong-lunchuan", color: "#03A9F4" },
        { icon: "iconktv", color: "#00BF96" },
        { icon: "iconlife", color: "#00BF96" },
        { icon: "iconliren", color: "#FF4081" },
        { icon: "iconmarried", color: "#FF4081" },
        { icon: "iconchild", color: "#FF4081" },
        { icon: "iconsport", color: "#03A9F4" },
        { icon: "icondecorate", color: "#00BF96" },
        { icon: "iconeducation", color: "#00BF96" },
        { icon: "iconmedical", color: "#03A9F4" },
        { icon: "iconbar", color: "#00BF96" }
      ],
      
    };
  },
  components: {
    tone
  },
  methods: {},
  // asyncData(ctx) {
  //   return ctx.$axios.get('/menu').then(res=>{
  //     console.log(res.data.data);

  //   });
  // },

  async asyncData(ctx) {
    let [res1, res2, res3] = await Promise.all([
      ctx.$axios.get("/position"),
      ctx.$axios.get("/banner"),
      ctx.$axios.get("/menu")
    ]);
    // console.log(res2.data.data);
    ctx.store.state.location = JSON.parse(res1.data.data);
    return {
      menu: res3.data.data.menu,
      banner: res2.data.data
    };

    // console.log(res2);
    // console.log(res3);
  },
  mounted() {},
  watch: {},
  computed: {}
};
</script>

<style scoped lang='scss'>
.line {
  box-shadow: 2px 2px 2px #e2e2e2;
}
.head {
  display: flex;
}
.all {
  width: 20%;
  border: 1px solid #e2e2e2;
  border-bottom: 0;
  display: flex;
  justify-content: space-between;
  height: 50px;
  line-height: 50px;
  color: #222222;
  font-size: 16px;
  font-weight: 700;
  padding-left: 15px;
}
.h-all {
  display: flex;
  justify-content: space-between;
  height: 50px;
  line-height: 50px;
  color: #222222;
  font-size: 16px;
  font-weight: 700;
  margin-left: 30px;
}
.w-all {
  display: -webkit-box;
  height: 425px;
}
.left {
  // flex: 1;
  width: 20%;
  // width: 228px;
  border: 1px solid #e2e2e2;
  .list {
    display: flex;
    justify-content: space-between;
    padding: 0 10px;
    position: relative;
    height: 26px;
    line-height: 26px;
    position: relative;
    .left1 {
      display: flex;
    }
    .hot {
      border-radius: 10px;
      background: #fff3cc;
      padding: 2px 6px;
      height: 20px;
      line-height: 16px;
      left: 80px;
      top: 4px;
      position: absolute;
    }
    .name {
      margin-left: 20px;
    }
    &:hover {
      background: #fff3cc;
      .lists {
        display: block;
      }
      .name {
        font-weight: bold;
      }
      .hot {
        background: #ffac38;
      }
    }
  }
  .arrow-forward {
    position: relative;
    top: 1px;
  }
  .lists {
    display: none;
    width: 400px;
    height: 425px;
    position: fixed;
    top: 196px;
    left: 348px;
    border: 1px solid #e2e2e2;
    z-index: 99;
    background: #fff;
    .wraps {
      width: 90%;
      margin: auto;
    }
    .head {
      display: flex;
      justify-content: space-between;
      height: 50px;
      line-height: 50px;
      border-bottom: 1px solid #e2e2e2;
      .names {
        font-size: 20px;
        color: #666;
      }
    }
    .item {
      display: flex;
      flex-wrap: wrap;

      .items {
        margin: 5px 10px;
        margin-left: 0;
      }
    }
  }
}
.center {
  // flex: 3;
  width: 80%;
  .top {
    display: flex;
    height: 240px;
  }
  .banner {
    // flex: 4;
    margin: 10px;
    .img {
      width: 100%;
    }
  }
  .c-r {
    // flex: 1;
    margin: 10px;
    margin-left: 0;
    img {
      width: 100%;
    }
  }
  .bottom {
    display: flex;
    height: 165px;
    .b-two {
      display: flex;
      margin: 10px;
    }
    .b-img {
      display: flex;
      .bb-img {
        // flex: 2;
        margin: 10px;
        margin-left: 0;
        width: 270px;
        img {
          width: 100%;
          margin: auto;
        }
      }
    }
    .b-r {
      // flex: 1;
      margin: 20px 0 0 -10px;

      img {
        width: 100%;
      }
    }
  }
  .c-third {
    border: 1px solid #e2e2e2;
    margin: 10px 0 10px 0;
    // margin-left: 0;
    width: 100%;
    height: 100%;
    padding-top: 30px;
    .avatar {
      border-radius: 30px;
      margin: auto;
      img {
        width: 47px;
        height: 47px;
        border-radius: 50%;
        border: 4px solid #e5e5e5;
        margin: auto;
      }
    }
    .hi {
      font-size: 16px;
      color: #222;
      text-align: center;
      font-weight: 500;
      margin: 15px 0;
    }
    .register {
      width: 118px;
      text-align: center;
      margin: 10px auto 15px auto;
      border: 1px solid #e5e5e5;
      border-radius: 40px;
      font-size: 14px;
      color: #333;
      transition: background-color 0.5s;
      display: block;
      line-height: 38px;
    }
  }
  .c-b-third {
    border: 1px solid #e2e2e2;
    margin: 20px 0 0 10px;
    width: 100%;
    height: 100%;
    .erweima {
      img {
        width: 95px;
        height: 95px;
        margin: 10px auto 0 auto;
      }
    }
    .phone {
        font-size: 16px;
        color: #222222;
        font-weight: 500;
        text-align: center;
      }
      .red {
        color: #ec5330;
        margin-right: 5px;
      }
  }
}
@media screen and (max-width: 1200px) {
  .c-r,
  .b-r {
    display: none;
  }
  .c-b-third {
    margin: 20px 0 0 -10px !important;
  }
  .wrap {
    width: 940px !important;
    margin: auto !important;
  }
}
</style>