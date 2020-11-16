<template>
  <div id="Subscription">
    <toast
      v-model="showPositionValue"
      type="text"
      :time="2000"
      width="20em"
      is-show-mask
      :text="toastText"
      position="center"
    ></toast>
    <h1>ZN Lib: Become a member, read freely without limit!</h1>
    <div class="message">
      为了提供更好的阅读体验,我们开发了付费订阅板块,他不同于Hot推荐板块,本版块专注于为每
      一位会员提供私人定制般的服务,拥有更加完美的阅读体验当然,大大需要为此支付一小丢丢的铜
      板,毕竟我们也是要恰饭的啦~以下就来为大大讲解一下成为会员的优势吧!
    </div>
    <div class="container">
      <div class="card">
        <div class="face face1">
          <div class="content">
            <img src="../../static/images/Free-Tag 2.png" />
            <h3>All Free</h3>
          </div>
        </div>
        <div class="face face2">
          <div class="content">
            <p>Need to pay to watch the content, VIP members can watch for free, from now on no longer for some content need special fees and in the annoyance ~ become a member, read the massive wonderful content, more can watch more front-line Revelations in advance!</p>
          </div>
        </div>
      </div>
      <div class="card">
        <div class="face face1">
          <div class="content">
            <img src="../../static/images/vip1.png" />
            <h3>Beautiful pendant</h3>
          </div>
        </div>
        <div class="face face2">
          <div class="content">
            <p>Members can get exclusive pendants free of charge for dressing up themselves, and the pendants with VIP status can be displayed in the comment area, personal space and other places to fully show their VIP status. You can't buy them even if you have money.</p>
          </div>
        </div>
      </div>
      <div class="card">
        <div class="face face1">
          <div class="content">
            <img src="../../static/images/count.png" />
            <h3>Goods discount</h3>
          </div>
        </div>
        <div class="face face2">
          <div class="content">
            <p>Member period, all items of the House Man Mall enjoy 10% off treatment, and all shipping costs by the studio free, from now on no longer have to worry about shipping costs! More limited when the membership exclusive activities and so you come to participate in oh</p>
          </div>
        </div>
      </div>
      <div class="card">
        <div class="face face1">
          <div class="content">
            <img src="../../static/images/数据 (1).png" />
            <h3>Accurate recommendation</h3>
          </div>
        </div>
        <div class="face face2">
          <div class="content">
            <p>There is the studio dedicated to create the data analysis precision recommendation function, members can view their interest in real time can also enjoy the precision recommendation function, from then on completely away from the book shortage!</p>
          </div>
        </div>
      </div>
    </div>
    <div
      class="message"
    >相信大大在看完介绍后,一定会对会员的优势动心了吧?不用担心,我们提供的费用并不高,下面是付费套餐,正值小店刚刚开业起步,我们为大大提供了折扣哦~现在不买,更待何时呢?</div>
    <div class="top-up">
      <div class="info">
        <div class="me">
          <img :src="account" />
        </div>
        <p class="name">{{name}}</p>
        <p class="status">{{status?`您已经成为会员,请点击下方按钮进入订阅空间~`:`您还不是会员,请先选择套餐进行付费订阅~`}}</p>
        <p class="exchange">邀请码开通</p>
      </div>
      <div class="choose">
        <div class="box" @click="check(0)">
          <p>连续包年</p>
          <h2>￥148</h2>
          <del>￥233</del>
        </div>
        <div class="box" @click="check(1)">
          <p>连续包季</p>
          <h2>￥45</h2>
          <del>￥68</del>
        </div>
        <div class="box" @click="check(2)">
          <p>连续包月</p>
          <h2>￥15</h2>
          <del>￥25</del>
        </div>
        <div class="box" @click="check(3)">
          <p>年度会员</p>
          <h2>￥168</h2>
          <del>￥233</del>
        </div>
        <div class="box" @click="check(4)">
          <p>季度会员</p>
          <h2>￥58</h2>
          <del>￥68</del>
        </div>
        <div class="box" @click="check(5)">
          <p>月度会员</p>
          <h2>￥25</h2>
          <p>&nbsp;</p>
        </div>
      </div>
      <p class="intro">{{text}}</p>
      <div class="qrcode">
        <div class="paymethod">
          <div class="animation"></div>
          <p class="method" @click="pay(0)">QQ支付</p>
          <p class="method" @click="pay(1)">微信支付</p>
          <p class="method" @click="pay(2)">支付宝支付</p>
        </div>
        <div class="cover">
          <img src="../../static/images/刷新.png" />
        </div>
        <div class="paycode">
          <img :src="qrcode" />
        </div>
        <p class="money">￥{{money}}</p>
        <p class="hint">{{hint}}</p>
      </div>
      <div class="agreement">
        <input type="checkbox" id="agree" @click="hide" />同意
        <a>《会员服务协议》</a>
        <a>《会员自动服务规则》</a>
      </div>
    </div>
    <div class="myzone">
      <div class="button" @click="enter">Enter My Zone</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Subscription",
  data() {
    return {
      name: "",
      status: false,
      account: `../../static/images/account.png`,
      hint: `请先阅读并同意协议`,
      qrcode: "../../static/images/qqqrcode.png",
      money: 148,
      text: `每年按148元自动续费，可随时取消`,
      toastText: ``,
      showPositionValue: false
    };
  },
  mounted: function() {
    this.getRouterData();
  },
  methods: {
    check(i) {
      $(".choose .box").css("border", "1px #737373 solid");
      $(".choose .box")
        .eq(i)
        .css("border", "1.5px silver solid");
      switch (i) {
        case 0:
          this.text = `每年按148元自动续费，可随时取消`;
          this.money = 148;
          this.choose(i);
          break;
        case 1:
          this.text = `每季按45元自动续费，可随时取消`;
          this.money = 45;
          this.choose(i);
          break;
        case 2:
          this.text = `每月按15元自动续费，可随时取消`;
          this.money = 15;
          this.choose(i);
          break;
        case 3:
          this.text = `12个月会员，限时优惠14元/月`;
          this.money = 168;
          this.choose(i);
          break;
        case 4:
          this.text = `3个月大会员，连续包季立省23元`;
          this.money = 58;
          this.choose(i);
          break;
        default:
          this.text = `1个月大会员，连续包月立省10元`;
          this.money = 25;
          this.choose(i);
          break;
      }
    },
    choose(i) {
      $(".box h2").css("color", "#737373");
      $(".box h2")
        .eq(i)
        .css("color", "#fff");
    },
    pay(i) {
      switch (i) {
        case 0:
          $(".qrcode .animation").css("top", "6.5%");
          this.qrcode = "../../static/images/qqqrcode.png";
          break;
        case 1:
          $(".qrcode .animation").css("top", "39.5%");
          this.qrcode = "../../static/images/wechatqrcode.png";
          break;
        default:
          $(".qrcode .animation").css("top", "72.5%");
          this.qrcode = "../../static/images/zhifubaoqrcode.jpg";
          break;
      }
    },
    hide() {
      if (document.getElementById("agree").checked) {
        $(".cover").css("opacity", "0");
        $(".cover").css("visibility", "hidden");
        this.hint = `请扫描二维码进行支付`;
      } else {
        $(".cover").css("opacity", "0.9");
        $(".cover").css("visibility", "visible");
        this.hint = `请先阅读并同意协议`;
      }
    },
    getRouterData() {
      this.account = this.$route.params.account;
      this.name = this.$route.params.name;
      this.status = this.$route.params.status;
    },
    enter() {
      if (this.status) {
        this.$router.push("/SubscriptionV");
        (function smoothscroll() {
          var currentScroll =
            document.documentElement.scrollTop || document.body.scrollTop;
          if (currentScroll > 500) {
            window.requestAnimationFrame(smoothscroll);
            window.scrollTo(0, currentScroll - currentScroll / 35);
          }
        })();
      } else {
        this.toastText = "抱歉,只有会员才可进入哦~";
        this.showPositionValue = true;
      }
    }
  }
};
</script>

<style scoped>
#Subscription {
  margin: 0 auto;
  margin-top: 50px;
  position: relative;
  width: 759.6px;
  min-height: 100vh;
}
#Subscription h1 {
  margin: 0 auto;
  margin-bottom: 50px;
  padding-top: 30px;
  font-size: 30px;
  font-weight: 500;
  color: white;
}
.message {
  width: 100%;
  position: relative;
  padding-left: 15px;
  border-left: 2px solid #fd281a;
  box-sizing: border-box;
  text-align: justify;
  line-height: 160%;
  font-size: 18px;
  color: #7f7f7f;
  letter-spacing: 1.1;
  padding-top: 30px;
}
.message::after {
  content: "“";
  position: absolute;
  left: -5px;
  top: 0px;
  font-size: 38px;
  color: #fd281a;
}
.container {
  margin: 0 auto;
  margin-top: 40px;
  width: 100%;
  position: relative;
  display: flex;
  justify-content: space-around;
  align-items: center;
  flex-wrap: wrap;
}
.container .card {
  position: relative;
  display: flex;
  margin-block-end: 30px;
  cursor: pointer;
}

.container .card .face {
  width: 400px;
  height: 200px;
  transition: 0.5s;
}
.container .card .face.face1 {
  position: relative;
  background: #333;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1;
  transform: translateX(200px);
}
.container .card:nth-child(odd):hover .face.face1 {
  transform: translateX(0px);
  transition-delay: 0.5s;
  background: #ff0057;
  box-shadow: 0 20px 50px rgba(0, 0, 0, 0.8);
}
.container .card:nth-child(even):hover .face.face1 {
  transform: translateX(400px);
  transition-delay: 0.5s;
  background: #00af64;
  box-shadow: 0 20px 50px rgba(0, 0, 0, 0.8);
}
.container .card .face.face1 .content {
  display: flex;
  flex-direction: column;
  align-items: center;
  opacity: 0.2;
  transition: 0.5s;
}
.container .card:hover .face.face1 .content {
  opacity: 1;
}
.container .card .face.face1 .content img {
  width: 50px;
}
.container .card .face.face1 .content h3 {
  margin: 10px 0 0;
  padding: 0;
  color: #fff;
  text-align: center;
  font-size: 1.5em;
}
.container .card .face.face2 {
  position: relative;
  background: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
  box-sizing: border-box;
  box-shadow: inset 0 20px 50px rgba(0, 0, 0, 0.8);
  transform: translateX(-200px);
}
.container .card:nth-child(odd):hover .face.face2 {
  transition-delay: 0.5s;
  transform: translateX(0px);
}
.container .card:nth-child(even):hover .face.face2 {
  transition-delay: 0.5s;
  transform: translateX(-400px);
}
.container .card .face.face2 .content p {
  transition: 0.6s;
  overflow: hidden;
  margin: 0;
  padding: 0;
}
.container .card:hover .face.face2 p {
  transition-delay: 0.5s;
  opacity: 1;
  height: inherit;
}
.top-up {
  width: 100%;
  padding-bottom: 20px;
  margin-top: 40px;
}
.info {
  width: 100%;
  height: 60px;
  position: relative;
  cursor: default;
}
.info .me {
  position: absolute;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  overflow: hidden;
  border: 1px #333 solid;
}
.info .name {
  color: #737373;
  position: absolute;
  left: 60px;
  margin: 0;
  top: 3px;
}
.info .status {
  color: #737373;
  position: absolute;
  left: 60px;
  margin: 0;
  bottom: 15px;
}
.info .exchange {
  color: #737373;
  position: absolute;
  right: 60px;
  margin: 0;
  bottom: 15px;
  transition: 0.4s;
  cursor: pointer;
}
.info .exchange:hover {
  color: silver;
}
.info .me img {
  width: 50px;
  border-radius: 50%;
  object-fit: cover;
}
.choose {
  margin-top: 15px;
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
.box {
  border: 1px #737373 solid;
  position: relative;
  cursor: pointer;
  box-sizing: border-box;
  padding: 15px 5px;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  border-radius: 5px;
  width: 15%;
  height: 140px;
  margin-bottom: 10px;
}
.box:nth-child(1) {
  border: 1.5px silver solid;
}
.box:nth-child(1):before {
  content: "6.3折";
  color: #fff;
  font-size: 0.7em;
  position: absolute;
  background-color: #fd281a;
  border-radius: 10px;
  top: -8px;
  right: 1px;
  border: 3px transparent solid;
}
.box:nth-child(2):before {
  content: "6.6折";
  color: #fff;
  font-size: 0.7em;
  position: absolute;
  background-color: #fd281a;
  border-radius: 10px;
  top: -8px;
  right: 1px;
  border: 3px transparent solid;
}
.box:nth-child(3):before {
  content: "优惠";
  letter-spacing: 3px;
  color: #fff;
  font-size: 0.7em;
  position: absolute;
  background-color: #fd281a;
  border-radius: 10px;
  top: -8px;
  right: 1px;
  border: 3px transparent solid;
}
.box:nth-child(4):before {
  content: "限时";
  letter-spacing: 3px;
  color: #fff;
  font-size: 0.7em;
  position: absolute;
  background-color: #088a08;
  border-radius: 10px;
  top: -8px;
  right: 1px;
  border: 3px transparent solid;
}
.box:nth-child(5):before {
  content: "限时";
  letter-spacing: 3px;
  color: #fff;
  font-size: 0.7em;
  position: absolute;
  background-color: #088a08;
  border-radius: 10px;
  top: -8px;
  right: 1px;
  border: 3px transparent solid;
}
.box p {
  margin: 0;
  color: #737373;
}
.box:hover h2 {
  color: #fff !important;
}
.box h2 {
  transition: 0.4s;
  color: #737373;
  margin: 0;
}
.intro {
  margin-left: 8px;
  font-size: 0.8em;
  color: #fff;
}
.qrcode {
  width: 100%;
  height: 200px;
  border: 1px #737373 solid;
}
.qrcode {
  position: relative;
}
.paymethod {
  height: 100%;
  width: 110px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  position: relative;
}
.method {
  transition: 0.5s;
  z-index: 1;
  margin: 0;
  color: #737373;
  line-height: 66px;
  text-align: center;
  width: 100%;
  height: 33%;
  cursor: pointer;
}
.paycode {
  position: absolute;
  width: 150px;
  height: 150px;
  top: 50%;
  left: 50%;
  transform: translate(-90%, -50%);
}
.cover {
  position: absolute;
  width: 150px;
  height: 150px;
  top: 50%;
  left: 50%;
  transform: translate(-90%, -50%);
  z-index: 1;
  background: rgba(0, 0, 0, 0.8);
  display: flex;
  justify-content: center;
  align-items: center;
  transition: 0.5s;
}
.cover img {
  width: 45px;
}
.paycode img {
  opacity: 0.9;
  width: 100%;
  height: 100%;
}
.qrcode .animation {
  position: absolute;
  width: 90%;
  left: 5%;
  top: 6.5%;
  height: 20%;
  border-radius: 10px;
  background: silver;
  transition: 0.3s ease;
}
.money {
  position: absolute;
  margin: 0;
  color: #fff;
  font-size: 2.4em;
  font-weight: bolder;
  top: 35%;
  left: 55%;
}
.hint {
  position: absolute;
  margin: 0;
  color: #737373;
  font-size: 0.8em;
  top: 65%;
  left: 56%;
}
.agreement {
  color: #fff;
  font-size: 0.8em;
  margin-top: 10px;
  display: flex;
  justify-content: center;
}
.myzone {
  margin-top: 40px;
  position: relative;
  width: 100%;
  padding-bottom: 30px;
}
.myzone .button {
  cursor: pointer;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 270px;
  height: 60px;
  text-align: center;
  line-height: 60px;
  color: #fff;
  font-size: 24px;
  text-transform: uppercase;
  text-decoration: none;
  font-family: sans-serif;
  box-sizing: border-box;
  background: linear-gradient(90deg, #03a9f4, #f441a5, #ffeb3b, #03a9f4);
  background-size: 400%;
  border-radius: 30px;
  z-index: 1;
}
.myzone .button:hover {
  animation: animate 8s linear infinite;
}
@keyframes animate {
  0% {
    background-position: 0%;
  }
  100% {
    background-position: 400%;
  }
}
.myzone .button:before {
  content: "";
  position: absolute;
  top: -5px;
  left: -5px;
  right: -5px;
  bottom: -5px;
  z-index: -1;
  background: linear-gradient(90deg, #03a9f4, #f441a5, #ffeb3b, #03a9f4);
  background-size: 400%;
  border-radius: 40px;
  opacity: 0;
  transition: 0.5s;
}
.myzone .button:hover:before {
  filter: blur(20px);
  opacity: 1;
  animation: animate 8s linear infinite;
}
@media screen and (max-width: 780px) {
  #Subscription {
    width: 100%;
  }
  #Subscription h1 {
    font-size: 25px;
  }
  .container .card {
    flex-direction: column;
    align-items: center;
  }
  .container .card .face.face1 {
    transform: translateX(0px);
    transform: translateY(100px);
  }
  .container .card .face.face2 {
    transform: translateX(0px);
    transform: translateY(-100px);
  }
  .container .card:nth-child(odd):hover .face.face1 {
    transform: translateX(0px);
    transform: translateY(0px);
    transition-delay: 0.5s;
    background: #ff0057;
    box-shadow: 0 20px 50px rgba(0, 0, 0, 0.8);
  }
  .container .card:nth-child(even):hover .face.face1 {
    transform: translateX(0px);
    transform: translateY(0px);
    transition-delay: 0.5s;
    background: #00af64;
    box-shadow: 0 20px 50px rgba(0, 0, 0, 0.8);
  }
  .container .card:nth-child(even):hover .face.face2 {
    transition-delay: 0.5s;
    transform: translateX(0px);
    transform: translateY(0px);
  }
  .container .card:nth-child(odd):hover .face.face2 {
    transition-delay: 0.5s;
    transform: translateX(0px);
    transform: translateY(0px);
  }
  .message {
    width: 95%;
    margin: 0 auto;
  }
  .top-up {
    width: 95%;
    margin: 0 auto;
    margin-top: 40px;
  }
}
@media screen and (max-width: 560px) {
  .paycode {
    left: 60%;
  }
  .container .card{
    margin-bottom:30px;
  }
  .container .card .face.face2{
    height:0px;
    overflow: hidden;
    margin-bottom:30px;
  }
  .container .card:hover .face.face2{
    height:200px;
    overflow: hidden;
  }
  .cover {
    left: 60%;
  }
  .name{
    display:none;
  }
  .money {
    left: 65%;
  }
  .hint {
    left: 65%;
  }
  .exchange {
    display: none;
  }
  .container .card .face {
    width: 300px;
  }
  .choose .box{
    width:90px;
  }
  .paycode,.cover{
    width:90px;
    height:90px;
    top:30%;
    left:70%;
  }
  .money{
    font-size:20px;
    top:60%;
    left:50%;
  }
  .hint{
    font-size:12px;
    top:80%;
    left:45%;
  }
}
</style>