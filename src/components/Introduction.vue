<template>
  <div id="Introduction">
    <div class="article">
      <div class="header">
        <h2>工作室介绍</h2>
        <div class="time">
          <img src="../../static/images/日历.png" />
          <p>2020-07-22</p>
        </div>
      </div>
      <div class="article-main">
        <p>Since its establishment on December 31, 2019, Otaku Studio has launched outstanding products such as Seeker navigation page and Otaku library, whose quality has been widely praised by the public. Among them, the concept of "If a Otaku doesn't go out, he knows the world" first proposed by Otaku Studio has been recognized by the industry.</p>
        <h2>Otaku studio for room brand view</h2>
        <h3>Brand vitality</h3>
        <p>
          Brand vitality is what decides the future market state of the brand! Brand vitality originates from brand culture. Strong brand comes from its own strong culture; Weak brands depend on the basic characteristics of their weak culture. As an enterprise, product, service or even marketing in the context of homogenous and homogeneous business, the only condition that has distinct identification and can distinguish two brands from the same industry is: different cultural attributes and cultural demands. That is, the cultural source of the brand.
          Based on the brand building concept of exploring different cultural sources for independent brands, Otaku Studio creates unique cultural roots and core connotations for the brand in an intuitive and effective way, defines brand subordination of independent cultural attributes in essence, and endows the brand with strong vitality!!
        </p>
        <h3>Brand influence</h3>
        <p>
          Brand influence is the ability of a brand to develop, occupy and make profits in the market. Brand influence has become an important factor influencing customers' choice of goods. Brand power is the foundation of brand influence. Implementing brand strategy and creating brand influence has become an important key point of brand construction and communication.
          Otaku studio believes that the promotion of brand influence does not only depend on the depth and breadth of brand communication radiation, but more importantly the systematization and relevance of brand construction and planning, as well as the feasibility and aggregation of brand image packaging. Otaku Studio, focus on the two key links of brand promotion, brand image and communication strategy) and new way for chain planning strategy and execution, which pays attention to high house built its macro management, also focus on step-by-step implementation, construct ShiXiaoXing brand "chain integration operation", to raise its brand to a higher realm.
        </p>
        <h2>Brand productivity</h2>
        <p>The otaku studio is still in its infancy, with limited development staff and small investment and financial support. However, with the promotion of excellent products, it is growing step by step. The basic situation of the company is listed in the form below</p>
        <div class="table-wrap">
          <table>
            <tbody>
              <tr>
                <td>Headquarters location</td>
                <td>Wuqing District, Tianjin</td>
              </tr>
              <tr>
                <td>Scope of business</td>
                <td>Internet product development</td>
              </tr>
              <tr>
                <td>Studio size</td>
                <td>2 people & 3 npc</td>
              </tr>
              <tr>
                <td>The company slogan</td>
                <td>A small workshop where strength and appearance coexist</td>
              </tr>
            </tbody>
          </table>
        </div>
        <h2>Product installation and testing</h2>
        <p>
          Click here to install
          <a href="#">Seeker navigation page</a>
          <br />Installation Precautions:
          <br />First of all, download the file after decompression will have index.html, js and Css files, do not change the CSS and js file path, directly click on the html file to open the preview, if the picture is too slow to load, please wait patiently, where the weather preview function requires a network connection.
        </p>
        <p>
          Click here to install
          <a href="#">Otaku Library</a>
          <br />Installation Precautions:
          <br />Since you are using the VUE framework, you need to first download and unzip the files, then open the Library folder from the IDE, click terminal options, create a new terminal and enter instructions below
        </p>
        <pre v-highlight>
          <code class="javascript">
            npm run dev
          </code>
        </pre>
        <p>Then, if it loads successfully, the following command is displayed:</p>
        <pre v-highlight>
          <code class="javascript">
            Your application is running here: http://localhost:8080
          </code>
        </pre>
        <p>At this point hold down the ctrl key left click on the link to view, due to the use of the graph bed, the picture will load slower please wait.</p>
      </div>
      <div class="article-footer">
        <div class="next" @click="next">
          <img src="../../static/images/右箭头.png" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Introduction",
  props: {
    isKnight: Boolean
  },
  mounted: function() {
    if (this.isKnight) {
      this.parentMethod(0);
    } else {
      this.parentMethod(1);
    }
  },
  methods: {
    next() {
      this.$router.push("/Studio/Update");
    },
    parentMethod(i) {
      if (!i) {
        $(".article").css("background", "#1f1f1f");
        $(".article .header h2").css("color", "rgba(255, 255, 255, 0.6)");
        $(".article p").css("color", "rgba(255, 255, 255, 0.6)");
        $(".article .table-wrap table").css(
          "color",
          "rgba(255, 255, 255, 0.6)"
        );
        $(".article .article-main a").css("color", "rgb(182, 32 ,22)");
        $(".hljs").css("cssText", "opacity:0.5!important");
        $(".article .article-footer .next").hover(
          function() {
            $(".article .article-footer .next").css(
              "background",
              "rgb(182, 32, 22)"
            );
          },
          function() {
            $(".article .article-footer .next").css("background", "none");
          }
        );
      } else {
        $(".article").css("background", "#fff");
        $(".article .header h2").css("color", "#696969");
        $(".article p").css("color", "#1a1a1a");
        $(".article .table-wrap table").css("color", "#1a1a1a");
        $(".hljs").css("cssText", "opacity:1!important");
        $(".article .article-footer .next").hover(
          function() {
            $(".article .article-footer .next").css("background", "#0088cc");
          },
          function() {
            $(".article .article-footer .next").css("background", "none");
          }
        );
      }
    }
  }
};
</script>

<style scoped>
#Introduction {
  width: 100%;
  min-height: 300px;
  max-height: 100vh;
  overflow-y: scroll;
  overflow-x: hidden;
}
#Introduction::-webkit-scrollbar {
  width: 0px;
}
.article {
  position: relative;
  margin-top: 10px;
  width: 100%;
  min-height: 300px;
  background: #fff;
  border: 1px solid #d1d1d1;
  transition: 1s;
}
.article::before {
  content: "";
  position: absolute;
  left: -2px;
  top: 0px;
  width: 5px;
  height: 80px;
  background: #4d4d4d;
}
.article .header {
  display: flex;
  justify-content: space-between;
  padding: 30px 60px 15px 25px;
  padding-left: 7.6923%;
  align-items: center;
}
.article .header h2 {
  margin: 0px;
  color: #696969;
  margin-left: 0;
  font-weight: 400;
  line-height: 35px;
  font-size: 26px;
  transition: 1s;
}
.article .header .time img {
  height: 20px;
  margin-right: 8px;
}
.article .header .time {
  display: flex;
  align-items: center;
  height: 100%;
}
.article .header .time p {
  margin: 0px;
  letter-spacing: 2px;
  color: #999;
  transition: 1s;
}
.article .article-main {
  box-sizing: border-box;
  padding-right: 7.6923%;
  padding-left: 7.6923%;
}
.article .article-main p {
  text-align: justify;
  box-sizing: border-box;
  color: #1a1a1a;
  font-family: lucida grande, lucida sans unicode, lucida, helvetica,
    Hiragino Sans GB, Microsoft YaHei, WenQuanYi Micro Hei, sans-serif;
  font-size: 1rem;
  line-height: 1.8em;
}
.article .article-main h1,
.article .article-main h2,
.article .article-main h3,
.article .article-main h4,
.article .article-main h5 {
  margin-top: 20px;
  font-weight: 700;
  color: #574c4c;
  padding-bottom: 5px;
  border-bottom: 1px solid #ddd;
  text-transform: capitalize;
  font-family: lucida grande, lucida sans unicode, lucida, helvetica,
    Hiragino Sans GB, Microsoft YaHei, WenQuanYi Micro Hei, sans-serif;
  box-sizing: border-box;
}
.article .article-main a {
  text-decoration: none;
  color: #08c;
}
.table-wrap {
  margin: 0 0 1rem;
}
.table-wrap table {
  color: #1a1a1a;
  font-family: lucida grande, lucida sans unicode, lucida, helvetica,
    Hiragino Sans GB, Microsoft YaHei, WenQuanYi Micro Hei, sans-serif;
  font-size: 1rem;
  border-color: grey;
  overflow-wrap: break-word;
  display: table;
  width: 100%;
  border-spacing: 0;
  border-collapse: collapse;
  empty-cells: show;
}
.table-wrap table thead {
  background: rgba(153, 169, 191, 0.1);
  vertical-align: center;
}
.table-wrap table tr {
  box-sizing: border-box;
}
.table-wrap table td {
  display: table-cell;
}
.table-wrap table th,
.table-wrap table td {
  padding: 0.3rem 0.6rem;
  border: 1px solid #d6d6d6;
  vertical-align: middle;
}
.article .article-main pre {
  font-family: consolas, Menlo, "PingFang SC", "Microsoft YaHei", sans-serif;
  overflow-x: auto;
  font-size: 16px;
  font-weight: 700;
  line-height: 1.5;
}
.hljs {
  border-radius: 8px !important;
}
.article .article-footer {
  padding-top: 20px;
  margin: 30px 7.6923% 0;
  height: 80px;
  border-top: 1px solid #ddd;
  box-sizing: border-box;
  position: relative;
}
.article .article-footer .next {
  width: 35px;
  height: 35px;
  border-radius: 50%;
  transition: 0.7s;
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  right: 10px;
  cursor: pointer;
}
.article .article-footer .next:hover {
  background: #0088cc;
  filter: brightness(150%);
}
.article .article-footer .next img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
@media screen and (max-width: 800px) {
  #Introduction {
    max-height: initial;
    overflow: visible;
  }
}
@media screen and (max-width: 499px) {
  .article .article-main {
    padding-right: 3%;
    padding-left: 3%;
  }
  .article .article-main pre {
    font-size: 10px;
  }
}
</style>