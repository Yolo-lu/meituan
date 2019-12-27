<template>
  <div class="alls">
    <div class="head">
      <div class="tone">有格调</div>
      <div v-for="(item,index) in tab" :key="index">
        <div @mouseenter="mouseenter(item.keywords)">
          <div class="tab">{{item.name}}</div>
          <div class="delta" v-if="item.keywords===keywords">
            <Icon type="md-arrow-dropup" color="#fff" size="25" />
          </div>
        </div>
      </div>
    </div>
    <div class="pois">
      <div v-for="(item,index) in pois.slice(0,6)" :key="index" class="list">
        <div class="photo">
          <img :src="item.photos[0].url" alt />
        </div>
        <div class="name">{{item.name}}</div>
        <div class="type">{{type}}</div>
        <div class="b-list">
          <div class="price">
          <div v-if="item.biz_ext.cost.length>0">
            <span>￥</span>
            <span class="total-price">{{item.biz_ext.cost}}</span>
            <span>/起</span>
          </div>
          <div v-if="item.biz_ext.cost.length===0">
            <span>￥</span>
            <span class="total-price">0元</span>
            <span>/起</span>
          </div>
        </div>
        <div class="address">{{item.adname}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tab: [
        { name: "全部", keywords: "全部" },
        { name: "约会聚餐", keywords: "美食" },
        { name: "丽人spa", keywords: "丽人" },
        { name: "电影演出", keywords: "电影" },
        { name: "品质出游", keywords: "旅游" }
      ],
      keywords: "景点",
      pois: [],
      type: ""
    };
  },
  components: {},
  methods: {
    getData() {
      let city = this.location.city.replace("市", "");
      this.$axios
        .get(`/results?city=${city}&keyword=${this.keywords}`)
        .then(res => {
          console.log(res.data.data.pois);
          this.pois = res.data.data.pois;
          res.data.data.pois.map((item, index) => {
            this.type = item.type.slice(0, item.type.indexOf(";"));
            if (item.photos.length === 0) {
              res.data.data.pois.splice(index, 1);
            }
          });
        });
    },
    mouseenter(val) {
      this.keywords = val;
      this.getData();
    }
  },
  mounted() {
    this.getData();
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
.alls {
  margin-top: 30px;
  border: 1px solid #e2e2e2;
  width: 100%;
  border-radius: 5px 5px 0 0;
}
.head {
  display: flex;
  height: 44px;
  background: #c0a87c;
  font-size: 14px;
  color: #fff;
  border-radius: 5px 5px 0 0;
  .tone {
    line-height: 44px;
    font-size: 18px;
    margin-left: 13px;
    margin-right: 10px;
  }
  .tab {
    padding: 0 5px;
    line-height: 44px;
  }
  .delta {
    text-align: center;
    position: relative;
    top: -14px;
  }
}
.pois {
  display: flex;
  flex-wrap: wrap;
  .list {
    width: 33.3%;
    height: 314px;
    padding: 10px;
    .photo {
      height: 208px;
      img {
        width: 100%;
        height: 100%;
        border-radius: 4px;
      }
    }
    .name {
      font-size: 16px;
      color: #222;
      height: 22px;
      line-height: 22px;
      font-weight: 500;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
      cursor: pointer;
    }
    .price {
      color: #be9e4d;
      .total-price {
        font-size: 22px;
        color: #be9e4d;
        margin-right: 6px;
        letter-spacing: -0.8px;
        cursor: pointer;
        margin: 0 -2px;
      }
    }
    .type {
      height: 18px;
      line-height: 18px;
      text-align: center;
      border: 1px solid #d8d8d8;
      border-radius: 2px;
      padding: 0 3px;
      width: 80px;
    }
    .b-list{
      display: flex;
      justify-content: space-between;
      .address{
        font-size: 12px;
    color: #999;
        margin-top: 10px;
      }
    }
  }
}
</style>