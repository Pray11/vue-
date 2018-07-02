<template>
 <div class="course">
   <!-- 背景变黑 -->
  <div class="zz" v-show="window">
  </div>
  <!-- 弹窗 -->
  <div class="window" v-show="window">
    <div class="title">
      <img class="closeicon" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgBAMAAACBVGfHAAAAD1BMVEUAAACPlp6NlJiOlJqNlJn0uOiMAAAABHRSTlMAIeK/vYp1PgAAAG1JREFUKM9l0okJwCAQBdFNB2IqENJAIBWY/nsS5MMIE4iKPq9d6251fNdb3zg7+l99tgM8Y/+A2QqyQUpAKkBqAI0MQABpAkICIAGQAEgABECHpnhRbeuD6ei+nK7vACmEDrLSoEQplUq2nsMCTfQUD4T57q8AAAAASUVORK5CYII=" @click="close()">
      <h3>选择课程</h3>
      <h4>赶紧选择你要学习的课程吧</h4>
    </div>
    <div class="img">
      <div v-for="item in courselist" :style="change">
       <img class="img1" :src="item.url">
      </div>
    </div>
    <div>
      <img class="left" :src="left" @click="lefts()"/>
      <img class="right" :src="right" @click="rights()"/>
    </div>
  </div>
  <div class="main">
    <div>
      主要内容
    </div>
  
  </div>
 
 </div>
</template>

<script>
export default {
  data() {
    return {
      window: true, //弹窗展示与否
      left: require("./left.png"),
      right: require("./right.png"),
      courselist: [
        {
          url: require("./1.png")
        },
        {
          url: require("./2.png")
        },
        {
          url: require("./3.png")
        },
        {
          url: require("./1.png")
        },
        {
          url: require("./2.png")
        },
        {
          url: require("./3.png")
        },
        {
          url: require("./1.png")
        },
        {
          url: require("./2.png")
        },
        {
          url: require("./3.png")
        }
      ],
      change: "",
      a: 0,
      b: 0
    };
  },
  methods: {
    close() {
      this.window = !this.window;
    },
    lefts() {
      if (this.a + this.b == 0) {
        this.left = require("./right.png");
      } else {
        this.right = require("./right.png");
        this.a += 374;
        let c = this.a + this.b;
        let left = "transform:translateX(" + c + "px)";
        this.change = left;
        console.log(this.change)
      }
    },
    rights() {
      if (this.a + this.b == -374 * (this.courselist.length - 3)) {
        this.right = require("./left.png");
      } else {
        this.left = require("./left.png");
        this.b += -374;
        let c = this.a + this.b;
        let right = "transform:translateX(" + c + "px)";
        this.change = right;
        console.log(this.change)
      }
    }
  }
};
</script>
<style scoped>
* {
  margin: 0;
  padding: 0;
}
.window {
  background-color: white;
  width: 1146px;
  height: 672px;
  z-index: 102;
  position: absolute;
  top: 179px;
  left: 50%;
  transform: translateX(-50%);
  text-align: center;
  overflow: hidden;
}
.title {
  margin-left: 24px;
}
.left {
  width: 40px;
  height: 40px;
  margin-top: 32px;
  cursor: pointer;
}
.right {
  width: 40px;
  height: 40px;
  margin-top: 32px;
  margin-left: 40px;
  cursor: pointer;
}
.img {
  margin-top: 20px;
  width: 7000px;
  height: 460px;
  padding-left: 12px;
  text-align: left;
}
.img div {
  text-align: left;
  display: inline-block;
   -webkit-transition-property: -webkit-transform;
  transition-property: transform;
  -webkit-transition-duration:1s;
  transition-duration: 1s;
}
.img1 {
  width: 350px;
  height: 460px;
  margin-right: 12px;
  margin-left: 12px;
  cursor:pointer;
}
.title h3 {
  width: 112px;
  font-size: 28px;
  font-family: AdobeHeitiStd-Regular;
  color: rgba(13, 20, 30, 1);
  line-height: 28px;
  margin-top: 24px;
  font-weight: 550;
}
.title h4 {
  width: 216px;
  line-height: 18px;
  font-size: 18px;
  font-family: AdobeHeitiStd-Regular;
  color: rgba(93, 100, 110, 1);
  margin-top: 10px;
  font-weight: 500;
}
.closeicon {
  float: right;
  width: 16px;
  height: 16px;
  display: absolute;
  margin-right: 24px;
}
.nowshow {
  text-align: center;
}
.zz {
  width: 100%;
  height: 100%;
  background-color: #000;
  filter: alpha(opacity=70);
  -moz-opacity: 0.7;
  opacity: 0.7;
  position: absolute;
  z-index: 100;
}
.main {
  height: 100%;
  width: 100%;
  font-size: 50px;
  background-color: yellow;
}
.course {
  width: 100%;
  height: 100%;
}
</style>