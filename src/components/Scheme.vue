<template>
  <div id="Scheme">
    <div class="main">
      <h1>特别策划：阅读特别策划躲避日常的枯乏！</h1>
      <div class="message">
        为了提供更好的阅读体验，我们开发了付费订阅板块，他不同于Hot推荐板块，本版块专注于为每
        一位会员提供私人定制般的服务，拥有更� 完美的阅读体验当然，大大需要为此支付一小丢丢的铜板，毕竟我们也是要恰饭的啦~下面就来为大大讲解一下成为会员的优势吧！
      </div>
      <div id="count">
        <h2>📈今日热度℃:</h2>
        <IOdometer class="iOdometer" :value="num" />
      </div>
      <div id="info">
        <div class="container">
          <div class="skills">
            <span class="Name">动漫前言</span>
            <div class="percent">
              <div class="progress" style="width:95%;"></div>
            </div>
            <span class="Value">95%</span>
          </div>
          <div class="skills">
            <span class="Name">绘画技巧</span>
            <div class="percent">
              <div class="progress" style="width:75%;"></div>
            </div>
            <span class="Value">75%</span>
          </div>
          <div class="skills">
            <span class="Name">结局探索</span>
            <div class="percent">
              <div class="progress" style="width:72%;"></div>
            </div>
            <span class="Value">72%</span>
          </div>
        </div>
      </div>
      <div id="posts">
        <h2>📰年度特别策划书</h2>
        <div class="post" v-for="idx in posts" :key="idx.url">
          <a>
            <p>More...</p>
          </a>
          <div class="imgbx">
            <img :src="idx.url" />
          </div>
          <div class="info">
            <div class="title">
              <ul>
                <li>
                  <span class="icon">📅</span>
                  {{idx.date}}
                </li>
                <li>
                  <span class="icon">✒️</span>
                  {{idx.count}}
                </li>
                <li>
                  <span class="icon">⏱️</span>
                  {{idx.time}}
                </li>
              </ul>
            </div>
            <div class="content">
              <h2>{{idx.title}}</h2>
              <p>{{idx.content}}</p>
            </div>
          </div>
        </div>
        <h2>🎙️策划师有话说</h2>
        <div class="wrapper">
          <div class="outer">
            <div class="card" style="--delay:-1;">
              <div class="content">
                <div class="img">
                  <img src="../../static/images/advisor1.jpg" alt />
                </div>
                <div class="details">
                  <span class="name">Sumit Kapoor</span>
                  <p>Frontend Developer</p>
                </div>
              </div>
              <a href="#">Follow</a>
            </div>
            <div class="card" style="--delay:0;">
              <div class="content">
                <div class="img">
                  <img src="../../static/images/advisor2.jpg" alt />
                </div>
                <div class="details">
                  <span class="name">Andrew Neil</span>
                  <p>YouTuber & Blogger</p>
                </div>
              </div>
              <a href="#">Follow</a>
            </div>
            <div class="card" style="--delay:1;">
              <div class="content">
                <div class="img">
                  <img src="../../static/images/advisor3.png" alt />
                </div>
                <div class="details">
                  <span class="name">Jasmine Carter</span>
                  <p>Freelancer & Vlogger</p>
                </div>
              </div>
              <a href="#">Follow</a>
            </div>
            <div class="card" style="--delay:2;">
              <div class="content">
                <div class="img">
                  <img src="../../static/images/advisor4.jpg" alt />
                </div>
                <div class="details">
                  <span class="name">Justin Chung</span>
                  <p>Backend Developer</p>
                </div>
              </div>
              <a href="#">Follow</a>
            </div>
            <div class="card" style="--delay:2;">
              <div class="content">
                <div class="img">
                  <img src="../../static/images/advisor5.jpg" alt />
                </div>
                <div class="details">
                  <span class="name">Adrina Calvo</span>
                  <p>Teacher & Advertiser</p>
                </div>
              </div>
              <a href="#">Follow</a>
            </div>
          </div>
        </div>
      </div>
      <div id="Bookcomment">
        <div class="main">
          <div class="logo">
            <img src="../../static/images/BBS.png" height="30px" />
            <h2>COMMENTS</h2>
          </div>
          <div class="comment" v-for="(comment,index) in comments" :key="index">
            <img class="pic" :src="comment.url" />
            <div class="content">
              <div class="time">{{comment.time}}</div>
              <div class="commentdetail">
                <p>
                  <b>{{comment.name}}</b>
                </p>
                <p id="index">
                  <small>{{comment.comment}}</small>
                </p>
              </div>
            </div>
          </div>
          <div class="givecomment">
            <div class="me">
              <img src="/static/images/author.jpg" width="60px" />
            </div>
            <input
              type="text"
              id="comment"
              name="comment"
              placeholder="Giving some advice to designers now!"
            />
            <button @click="submit">Submit</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import IOdometer from "vue-odometer";
import "odometer/themes/odometer-theme-default.css";
export default {
  name: "Scheme",
  components: {
    IOdometer
  },
  data() {
    return {
      comments: [
        {
          name: "Chong",
          url: "../../static/images/advisor4.jpg",
          comment: "The planners are to be commended for doing their best to create a better experience for their clients!",
          time: "2020-11-10"
        },
        {
          name: "PanYizhe",
          url: "../../static/images/advisor5.jpg",
          comment: "Oh my goodness, this UI is really breathtaking! I really love this site ^_^",
          time: "2021-3-20"
        },
        {
          name: "Jack.Pikerson",
          url: "../../static/images/advisor2.jpg",
          comment: "I'm so excited to see who this year's Planner of the Year will be. Is it the greatest Chong Chong?",
          time: "Yesterday"
        }
      ],
      num: 167093,
      posts: [
        {
          url: "../../static/images/slide5.png",
          date: "2021-4-12",
          count: "12k",
          time: "20min",
          title: "hahahah",
          content:
            "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaabbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbb"
        },
        {
          url: "../../static/images/slide4.jpg",
          date: "2021-4-12",
          count: "12k",
          time: "20min",
          title: "hahahah",
          content:
            "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaabbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbb"
        },
        {
          url: "../../static/images/slide2.png",
          date: "2021-4-12",
          count: "12k",
          time: "20min",
          title: "hahahah",
          content:
            "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaabbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbb"
        },
        {
          url: "../../static/images/slide1.png",
          date: "2021-4-12",
          count: "12k",
          time: "20min",
          title: "hahahah",
          content:
            "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaabbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbb"
        }
      ]
    };
  },
  mounted() {
    const that = this;
    setInterval(function() {
      that.num += Math.ceil(Math.random() * 10);
    }, 3000);
  },
  methods: {
    submit() {
      var _this = this;
      var content = document.getElementById("comment").value;
      var gc = document.getElementsByClassName("givecomment")[0];
      if (content.length > 0) {
        var mydate = new Date();
        var obj = {
          name: "Pengpenglang",
          url: "../../static/images/author.jpg",
          comment: content,
          time: mydate.toLocaleString()
        };
        _this.comments.push(obj);
      }
    }
  }
};
</script>

<style scoped>
#Scheme {
  width: 960px;
  min-height: 100vh;
  margin: 0 auto;
  padding-top: 40px;
  /*background:pink;*/
  position: relative;
}
.main {
  margin: 0 auto;
  /* background: pink; */
  width: 80%;
  min-height: 50vh;
  /*background:#fff;*/
}
#Scheme h1 {
  margin-left: 5px;
  margin-bottom: 50px;
  font-size: 30px;
  font-weight: 500;
  color: white;
}
#count {
  padding-top: 50px;
  color: aliceblue;
  margin: 0 auto;
  width: 300px;
  display: flex;
  justify-content: space-around;
  align-items: center;
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
.iOdometer {
  font-size: 25px;
  margin: 0;
}
#info {
  display: flex;
  justify-content: center;
  align-items: center;
  padding-bottom: 20px;
}
.container {
  position: relative;
  width: 500px;
}

h2 {
  color: #fff;
}

.container .skills {
  position: relative;
  display: flex;
  margin: 20px 0;
  padding: 24px 10px 18px;
  background: linear-gradient(#616161 0%, #333 10%, #222);
  border-radius: 8px;
  overflow: hidden;
  border: 2px solid #000;
  transition: 0.5s;
}

.container .skills :before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 50%;
  background: rgba(255, 255, 255, 0.1);
  z-index: 10;
}

.container .skills .Name {
  position: relative;
  width: 110px;
  text-align: right;
  color: #fff;
  margin-top: -2px;
  text-transform: uppercase;
}

.container .skills .Value {
  position: relative;
  width: 40px;
  text-align: left;
  color: #fff;
  margin-top: -2px;
  text-transform: uppercase;
}

.container .skills .percent {
  position: relative;
  width: calc(100% - 150px);
  height: 20px;
  margin: 0 10px;
  border-radius: 10px;
  background: #151515;
  box-shadow: inset 0 0 10px #000;
  overflow: hidden;
}

.container .skills .percent .progress {
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  border-radius: 10px;
  background: #fff;
  box-shadow: inset 0 0 2px #000;
  animation: animate 1s ease-in-out forwards;
}

@keyframes animate {
  from {
    width: 0;
  }
}

.container .skills:nth-child(1) .percent .progress {
  background: linear-gradient(45deg, #1fe6ff, #673ab7);
}

.container .skills:nth-child(2) .percent .progress {
  background: linear-gradient(45deg, #3bc0ff, #33ff00);
}

.container .skills:nth-child(3) .percent .progress {
  background: linear-gradient(45deg, #ffee54, #ff00ca);
}
#posts {
  display: flex;
  flex-direction: column;
  align-items: center;
}
#posts .post {
  position: relative;
  display: flex;
  border-radius: 0.5rem;
  width: 90%;
  height: 230px;
  margin-bottom: 40px;
  background: #333333;
  align-items: center;
  justify-content: space-between;
  box-shadow: 0 0.625rem 1.875rem -0.9375rem #000;
  transition: 0.5s;
}
#posts .post a:hover {
  transform: scale(1.04);
}
#posts .post a {
  transition: 0.2s;
  z-index: 20;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 86px;
  height: 42px;
  box-sizing: border-box;
  position: absolute;
  bottom: -5px;
  right: -7px;
  transform-style: preserve-3d;
  transform: translateZ(2rem);
  backface-visibility: hidden;
  padding: 0.3rem 1rem;
  border-radius: 1rem 0;
  color: #000;
  background-image: linear-gradient(
    to right,
    rgba(241, 139, 179, 0.8) 0,
    rgba(240, 163, 135, 0.8) 100%
  );
}
#posts .post a::before {
  position: absolute;
  display: block;
  content: "";
  transform-style: preserve-3d;
  transform: translateZ(-2rem);
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
  height: calc(100% - 1rem);
  width: calc(100% - 1rem);
  border-radius: 5rem;
  left: 0.5rem;
  top: 0.8rem;
  box-shadow: 0 0 0.6rem 0.6rem rgba(237, 110, 160, 0.3);
  background-color: rgba(237, 110, 160, 0.3);
}
#posts .post:hover {
  box-shadow: 0 0 2rem #000;
}
#posts .post:hover .imgbx img {
  opacity: 1;
  transform: scale(1.1) rotate(1deg);
}
#posts .post .imgbx {
  height: 100%;
  width: 300px;
  /* background:yellow; */
  border-radius: 0.5rem;
  overflow: hidden;
  clip-path: polygon(0% 0%, 80% 0%, 100% 100%, 0% 100%);
}
#posts .post .imgbx img {
  border-radius: 0.5rem;
  overflow: hidden;
  transition: 0.4s;
  opacity: 0.8;
  object-fit: cover;
  height: 100%;
}
#posts .post .info {
  position: relative;
  height: 100%;
  width: 60%;
  /* background:blue; */
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
#posts .post .info .title {
  width: 100%;
  height: 30px;
}
#posts .post .info ul {
  height: 100%;
  float: right;
  width: 90%;
  list-style: none;
  display: flex;
  align-items: center;
  margin: 0;
  padding: 0;
  justify-content: space-evenly;
}
#posts .post .info ul li {
  font-size: 12px;
  color: #aaa;
  letter-spacing: 2px;
}
#posts .post .info ul li,
icon {
  filter: brightness(90%);
  font-size: 13px;
}
#posts .post .info .content {
  cursor: default;
  width: 100%;
  height: 90%;
  box-sizing: border-box;
  padding: 10px 20px;
}
#posts .post .info .content h2 {
  color: rgba(237, 118, 137, 0.9);
  transition: 0.7s;
  cursor: pointer;
  margin: 0;
}
#posts .post .info .content h2:hover {
  color: #9cd0ed;
}
#posts .post .info .content p {
  text-align: justify;
  overflow: hidden;
  word-wrap: break-word;
  font-size: 1.05rem;
  color: #aaa;
  width: 90%;
  height: 90%;
  /* background: pink; */
}
#posts .post:nth-child(2n + 1) {
  flex-direction: row-reverse;
}

#posts .post:nth-child(2n + 1) .imgbx {
  clip-path: polygon(20% 0%, 100% 0%, 100% 100%, 0% 100%);
}
#posts .post:nth-child(2n + 1) .info ul {
  float: left;
}
#posts .post:nth-child(2n + 1) a {
  left: -7px;
  border-radius: 0 1rem;
}
.wrapper {
  width: 100%;
  min-height: 300px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.wrapper .outer {
  display: flex;
  align-items: center;
  justify-content: center;
}
.wrapper .card {
  background: #aaa;
  width: 430px;
  height: 60px;
  display: flex;
  align-items: center;
  padding: 20px;
  opacity: 0;
  pointer-events: none;
  position: absolute;
  justify-content: space-between;
  border-radius: 100px 20px 20px 100px;
  box-shadow: 0px 10px 15px rgba(0, 0, 0, 0.1);
  animation: float 15s linear infinite;
  animation-delay: calc(3s * var(--delay));
}
.outer:hover .card {
  animation-play-state: paused;
}
.wrapper .card:last-child {
  animation-delay: calc(-3s * var(--delay));
}
@keyframes float {
  0% {
    opacity: 0;
    transform: translateY(100%) scale(0.5);
  }
  5%,
  20% {
    opacity: 0.4;
    transform: translateY(100%) scale(0.7);
  }
  25%,
  40% {
    opacity: 1;
    pointer-events: auto;
    transform: translateY(0%) scale(1);
  }
  45%,
  60% {
    opacity: 0.4;
    transform: translateY(-100%) scale(0.7);
  }
  65%,
  100% {
    opacity: 0;
    transform: translateY(-100%) scale(0.5);
  }
}
.card .content {
  display: flex;
  align-items: center;
}
.wrapper .card .img {
  height: 80px;
  width: 80px;
  position: absolute;
  left: 0px;
  background: rgba(255, 255, 255, 0.7);
  border-radius: 50%;
  padding: 5px;
  box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.2);
}
.card .img img {
  height: 100%;
  width: 100%;
  border-radius: 50%;
  object-fit: cover;
}
.card .details {
  margin-left: 80px;
}
.details span {
  font-weight: 600;
  font-size: 18px;
}
.card a {
  text-decoration: none;
  padding: 7px 18px;
  border-radius: 25px;
  color: #fff;
  background: linear-gradient(
    to right,
    rgba(241, 139, 179, 0.8) 0,
    rgba(240, 163, 135, 0.8) 100%
  );
  transition: all 0.3s ease;
}
.card a:hover {
  transform: scale(0.94);
}
#Bookcomment {
  width: 100%;
  margin-top: 40px;
}
#Bookcomment .main {
  color: #aaa;
  position: relative;
  margin: 0 auto;
  width: 100%;
  box-sizing: border-box;
  background-color: #222;
  border-left: #aaa 2px solid;
  border-bottom: #aaa 2px solid;
  border-right: #aaa 2px solid;
  padding: 20px 20px 40px 20px;
}
#Bookcomment .main::before{
  content:"";
  position: absolute;
  top:0;
  left:0;
  height:2px;
  width:20%;
  background:#aaa;
}
#Bookcomment .main::after{
  content:"";
  position: absolute;
  top:0;
  right:0;
  height:2px;
  width:20%;
  background:#aaa;
}
#Bookcomment .logo {
  position: absolute;
  display: flex;
  top: -20px;
  left: 50%;
  transform: translateX(-50%);
  justify-content: space-around;
  align-items: center;
  width: 200px;
  height: 50px;
}
#Bookcomment button {
  position: absolute;
  bottom: -20px;
  border-radius: 1rem;
  border: 0;
  width: 90px;
  height: 40px;
  left: 50%;
  transform: translateX(-50%);
  filter: drop-shadow(1px 1px 4px grey);
  color: white;
  cursor: pointer;
  background: #1abc9c;
  transition: 1s;
}
#Bookcomment button:hover {
  background: #9cd0ed;
}
#Bookcomment .comment {
  display: flex;
  justify-content: space-around;
  align-items: center;
  width: 90%;
  min-height: 80px;
  margin: 0 auto;
  padding: 15px 0px;
}
#Bookcomment .pic {
  border-radius: 50%;
  width: 60px;
  height: 60px;
  background-size: 100%;
  background-repeat: no-repeat;
}
#Bookcomment .content {
  display: flex;
  flex-direction: row-reverse;
  justify-content: space-between;
  width: 80%;
  height: 60px;
  overflow: hidden;
  opacity: 0.8;
}
#Bookcomment .time {
  text-align: bottom;
  font-size: 10px;
}
#Bookcomment .commentdetail {
  width: 70%;
}
#Bookcomment .givecomment {
  display: flex;
  justify-content: space-around;
  align-items: center;
  position: relative;
  width: 100%;
  height: 180px;
  margin: 0 auto;
}
#Bookcomment .me {
  width: 60px;
  height: 60px;
}
#Bookcomment p {
  margin: 4px;
  font-size: 13px;
}
#Bookcomment input {
  border-radius: 0.5rem;
  width: 70%;
  height: 100px;
  overflow: hidden;
  font-size: 17px;
}
@media screen and (max-width: 790px) {
  #Scheme {
    padding-top: 0;
    width: 100%;
  }
  #Scheme h1 {
    font-size: 25px;
  }
  #posts .post .info {
    width: 60%;
  }
  #posts .post .info .title ul {
    width: 100%;
    font-size: 7px;
  }
  #posts .post .info .title ul .icon {
    font-size: 5px;
  }
  #posts .post .info .content p {
    width: 100%;
    overflow: hidden;
    height: 60%;
  }
  @media screen and (max-width: 560px) {
    #Scheme {
      padding-top: 0;
      width: 100%;
    }
    #Scheme h1 {
      font-size: 25px;
    }
    #posts .post .info .imgbx {
      display: none;
    }
    #posts .post .info {
      width: 100%;
    }
    .wrapper .card {
      width: 300px;
      height: 40px;
    }
    .wrapper .card .img {
      width: 70px;
      height: 70px;
    }
    .details span {
      font-size: 16px;
    }
    .wrapper p {
      margin: 0;
      font-size: 10px;
    }
  }
}
</style>