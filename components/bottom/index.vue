<template>
  <div>
    <div class="top">
      <div class="one">
        <div v-for="(item,index) in data1.slice(0,2)" :key="index" class="ones">
          <div class="item">
            <div class="title">{{item.title}}</div>
            <div class="list" v-for="(item1,index1) in item.list" :key="index1">
              <div class="list-name">{{item1}}</div>
            </div>
          </div>
        </div>
      </div>
      <div v-for="(item,index) in data1.slice(2,3)" :key="index" class="one">
        <div class="item">
          <div class="title">{{item.title}}</div>
          <div class="list" v-for="(item1,index1) in item.list" :key="index1">
            <div class="list-name">{{item1}}</div>
          </div>
        </div>
      </div>
      <div class="one">
        <div v-for="(item,index) in data1.slice(3,5)" :key="index" class="ones">
          <div class="item">
            <div class="title">{{item.title}}</div>
            <div class="list" v-for="(item1,index1) in item.list" :key="index1">
              <div class="list-name">{{item1}}</div>
            </div>
          </div>
        </div>
      </div>
      <div class="one">
        <div v-for="(item,index) in data1.slice(5,8)" :key="index" class="ones">
          <div class="item">
            <div class="title">{{item.title}}</div>
            <div class="list" v-for="(item1,index1) in item.list" :key="index1">
              <div class="list-name">{{item1}}</div>
            </div>
          </div>
        </div>
      </div>
      <div class="one">
        <div v-for="(item,index) in data1.slice(8)" :key="index" class="ones">
          <div class="item">
            <div class="title">{{item.title}}</div>
            <div class="list" v-for="(item1,index1) in item.list" :key="index1">
              <div class="list-name">{{item1}}</div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="footer">
      <div class="left">
        <div class="l-item" v-for="(item,index) in data2" :key="index">
          <div class="name">{{item}}</div>
        </div>
      </div>
      <div class="right">
          <div class="rights">京公网安备11010502025545号</div>
          <div class="r-bottom">
            <div v-for="(item,index) in data3" :key="index">
              <div style="display:flex">
                <span>
                  <img :src="item.src" alt class="img"/>
                </span>
                <span v-if="item.text" class="l-item" style="line-height:38px">{{item.text}}</span>
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
      data1: [
        {
          title: "用户帮助",
          list: [
            "申请退款",
            "查看美团券密码",
            "常见问题",
            "用户协议",
            "隐私政策",
            "反诈骗公告",
            "消费者权益保障"
          ]
        },
        {
          title: "美团服务",
          list: [
            "美团外卖",
            "美团酒店",
            "猫眼电影",
            "美团配送",
            "美团云",
            "大众点评",
            "美团民宿",
            "无人配送"
          ]
        },
        {
          title: "商家合作",
          list: [
            "美团餐饮商户中心",
            "美食商家入驻(非外卖)",
            "美团外卖开店申请",
            "美团收银官网",
            "外卖配送加盟申请",
            "美团点评餐饮学院",
            "酒店商家入驻",
            "境内度假商家入驻",
            "综合商家入驻",
            "美团民宿房东商家入驻",
            "商家开票申请",
            "美团点评智能收银机",
            "美团点评餐饮开放平台",
            "美团点评收单",
            "免费使用美团排队",
            "快驴进货商家合作",
            "美团闪购商家入驻"
          ]
        },
        {
          title: "代理商加盟",
          list: [
            "美团外卖代理商招募",
            "到店餐饮代理商招募",
            "非餐饮代理商招募",
            "美团联盟",
            "美团收银招募线上分销商",
            "美团点评5S服务商招募",
            "美团收单渠道代理商招募"
          ]
        },
        {
          title: "美团规则",
          list: ["规则中心", "规则目录", "规则评议院"]
        },
        {
          title: "关注美团",
          list: ["美团新浪微博"]
        },
        {
          title: "公司信息",
          list: [
            "关于我们",
            "投资者关系",
            "加入我们",
            "商户诚信公约及管理办法",
            "保险经纪资质"
          ]
        },
        {
          title: "廉正举报",
          list: ["廉政邮箱"]
        },
        {
          title: "知识产权",
          list: ["知识产权维权平台"]
        },
        {
          title: "消费者服务热线",
          list: [
            "外卖消费者：10109777",
            "猫眼消费者：10105335",
            "其他消费者：10107888"
          ]
        },
        {
          title: "商家服务热线",
          list: [
            "外卖&餐饮商家：10105557",
            "休闲娱乐、丽人、ktv、教育、结婚、亲子、家装等商家：10100107"
          ]
        },
        {
          title: "投诉举报热线",
          list: [
            "违法和不良信息举报电话：4006018900",
            "举报邮箱：tousujubao@meituan.com"
          ]
        },
        {
          title: "商家自助入驻美团入口"
        },
        {
          title: "供应商注册入口"
        }
      ],
      data2: [
        "©美团网团购 meituan.com",
        "京ICP证070791号",
        "京ICP备10211739号",
        "广播电视节目制作经营许可证（京）字第03889号",
        "食品经营许可证",
        "互联网药品信息服务资格证",
        "医疗器械网络交易服务第三方平台备案：（京）网械平台备字[2018]第00004号"
      ],
      data3: [
        {
          src:
            "https://p1.meituan.net/travelcube/3e7f8a17e55bace814166b667618b459366061.png@76h_76w_2e",
          text: "北京三快科技有限公司"
        },
        { src: require("../../assets/images/website.png")},
        { src: require("../../assets/images/kexin.png") },
        { src: require("../../assets/images/12315.png") }
      ]
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
.top {
  display: flex;
  flex-wrap: wrap;
  margin-top: 50px;
  padding: 40px 45px;
  border-top: 1px solid #e5e5e5;
  border-bottom: 1px solid #e5e5e5;
}
.one {
  width: 20%;
  .ones {
    margin-bottom: 25px;
  }
  .title {
    color: #333;
    font-size: 14px;
    font-weight: 500;
  }
  .list {
    color: #666;
  }
}
.footer {
  display: flex;
  justify-content: space-between;
  margin: 20px 0;
}
.left {
  width: 45%;
  display: flex;
  flex-wrap: wrap;
 
}
 .l-item {
    margin: 1px 4px;
    color: #999;
    line-height: 1.6;
  }
.right{
  width: 53%;
  position: relative;
  .rights{
    position: absolute;
      right: 0px;
       margin: 1px 4px;
    color: #999;
    }
  .r-bottom {
    position: absolute;
      right: 0px;
    display: flex;
    margin-top: 30px;
    .img{
      height: 38px;
    }
    
  }
}
.list-name,.name{
  &:hover {
   color: #fe8c00 !important;
  }
}
</style>