<template>
  <div>
    <div class="search">
      <div class="left">
        <img src="../../assets/images/logo.png" alt />
      </div>
      <div class="right">
        <div class="inputs">
          <input type="text" placeholder="搜索商家或地点" @focus="focus" @blur="blur" />
          <div class="icon">
            <div class="s-icon">
              <Icon type="ios-search" size="30" />
            </div>
          </div>
        </div>
        <div class="hotPlace">
          <div v-for="(item,index) in hotPlace.slice(0,5)" :key="index">
            <div>{{item.name}}</div>
          </div>
        </div>
        <div class="hot-search" v-if="lock">
          <div class="one">
            <div class="last">最近搜索</div>
            <div class="del">删除搜索历史</div>
          </div>
          <div class="two">
            <div class="last">热门搜索</div>
            <div class="hot">
              <div v-for="(item,index) in hotPlace.slice(0,5)" :key="index">
            <div class="names">{{item.name}}</div>
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
    return {
      hotPlace: [],
      lock: false //控制热门搜索框
    };
  },
  components: {},
  methods: {
    search() {
      let city = this.location.city.replace("市", "");
      this.$axios.get(`hotPlace?city=${city}`).then(res => {
        this.hotPlace = res.data.data.result;
        //   console.log(res.data.data);
      });
    },
    focus() {
      this.lock = true;
    },
    blur(){
      this.lock = false;
    }
  },
  mounted() {
    this.search();
  },
  watch: {},
  computed: {
    location() {
      return this.$store.state.location;
    }
  }
};
</script>

<style scoped lang='scss'>
.search {
  display: flex;
  margin-top: 30px;
  // height: 140px;
  .left {
    img {
      width: 126px;
      height: 46px;
    }
  }
  .right {
    margin-left: 130px;
    position: relative;
    .inputs {
      height: 40px;
      display: flex;
      input {
        padding: 10px;
        line-height: 38px;
        width: 470px;
      }
    }
    .icon {
      width: 80px;
      height: 40px;
      background: #ffc300;
      border-radius: 0 5px 5px 0;
      .s-icon {
        text-align: center;
        line-height: 40px;
      }
    }
    .hotPlace {
      display: flex;
      color: #999;
      div {
        margin: 5px;
        &:hover {
          color: #fe8c00;
        }
      }
    }
    .hot-search{
  width: 470px;
  // height: 126px;
  border: solid 1px #e2e2e2;
  position: absolute;
  top: 40px;
  z-index: 99;
  background: #fff;
  border-radius: 0 0 5px 5px;
  padding: 0 10px;
    .one{
      display:flex;
      justify-content: space-between;
      margin: 5px 0
    }
    .two{
      margin: 5px 0
    }
    .last{
          color: #999;
          font-weight: bold;
         
    }
     .hot{
            display: flex;
            .names{
              margin: 0 5px;
              &:first-child {
                margin-left: 0 !important;
              }
            }
          }
    }
    
    
  }
}
</style>