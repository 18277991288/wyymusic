<template>
  <div id="Home" class="wrapper" ref="wrapper">
    <div class="PlazaTop">个人设置</div>
    <Scroll :probeType="3" class="content" ref="scroll">
      <van-pull-refresh
        v-model="isLoading"
        @refresh="onRefresh"
        success-text="刷新成功"
      >
      <div class="MineTop">
        <div class="pic"><img src="~assets/img/yu.jpg" alt=""></div>
        <div class="username">陶星宇</div>
        <div class="details" @click="showPopup">个人主页<img src="~assets/img/mine/right.png" alt=""></div>
      </div>

      <div class="MineMid" @click="LiClick">
        <ul>
          <li><img src="~assets/img/mine/song.png" alt=""><p>我的音乐</p></li>
          <li><img src="~assets/img/mine/download.png" alt=""><p>我的下载</p></li>
          <li><img src="~assets/img/mine/play.png" alt=""><p>最近播放</p></li>
          <li><img src="~assets/img/mine/like.png" alt=""><p>收藏和赞</p></li>
          <li><img src="~assets/img/mine/vip.png" alt=""><p>会员中心</p></li>
          <li><img src="~assets/img/mine/buy.png" alt=""><p>音乐商城</p></li>
          <li><img src="~assets/img/mine/video.png" alt=""><p>音乐电台</p></li>
          <li><img src="~assets/img/mine/sao.png" alt=""><p>扫一扫</p></li>
        </ul>
      </div>

      <div class="MineLow" @click="showPopup">
        <div class="top">设置</div>
        <div class="list">
          <p>动态隐私设置</p>
          <img src="../../assets/img/mine/right1.png" alt="">
        </div>
        <div class="list">
          <p>通知</p>
          <img src="../../assets/img/mine/right1.png" alt="">
        </div>
        <div class="top">系统</div>
        <div class="list">
          <p>语言</p>
          <img src="../../assets/img/mine/right1.png" alt="">
        </div>
        <div class="list">
          <p>清除缓存</p>
          <img src="../../assets/img/mine/right1.png" alt="">
        </div>
        <div class="list">
          <p>疑问与常见问题</p>
          <img src="../../assets/img/mine/right1.png" alt="">
        </div>
        <div class="list">
          <p>版本说明</p>
          <img src="../../assets/img/mine/right1.png" alt="">
        </div>
        <div class="list">
          <p>关于我们</p>
          <img src="../../assets/img/mine/right1.png" alt="">
        </div>
      </div>
      </van-pull-refresh>
      <div class="kong"></div>
    </Scroll>
    <van-popup v-model="show" class="popup" position="right" closeable :overlay="false">
      <img src="../../assets/img/mine/sorry.jpg" alt="">
      <h3>还未开发</h3>
    </van-popup>
  </div>
</template>

<script>

import Scroll from "components/common/Scroll";
import { PullRefresh } from "vant";
import { Uploader } from 'vant';
import { Popup } from "vant";

export default {
  name: "Home",
  components: {
    Scroll,
    [Uploader.name]: Uploader,
    [PullRefresh.name]: PullRefresh,
    [Popup.name]: Popup,
  },
  mounted() {
    this.initScroll();
  },
  activated() {
    this.initScroll();
  },
  data() {
    return {
      isLoading: false,
      show: false,
    };
  },
  methods: {
    onRefresh() {
      setTimeout(() => {
        this.isLoading = false;
        // console.log(this.count);
        if (this.count < 9) {
          this.count++;
          // this.$refs.personalized.getPersonalized(this.count * 6,(this.count + 1) * 6);
        } else {
          this.count = 0;
          // this.$refs.personalized.getPersonalized(this.count * 6,(this.count + 1) * 6);
        }
        this.initScroll();
      }, 1000);
    },
    
    initScroll() {
      this.$nextTick(() => {
        this.$refs.scroll.scroll.refresh();
      });
    },
    showPopup() {
      this.show = true;
    },
    LiClick() {
      this.$message('未开发~');
    },
    
  },
};
</script>

<style scoped>
#home {
  position: relative;
  overflow: hidden;
}
.content {
  height: calc(100vh - 90px);
  overflow: hidden;
  position: absolute;
  top: 49px;
  bottom: 0px;
  left: 0;
  right: 0;
  overflow: hidden;
}
.kong {
  height: 50px;
}
.PlazaTop {
  width: 100%;
  height: 49px;
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  z-index: 999;
  background: #fff;
  color: rgb(100, 208, 156);
  font-size: 17px;
  align-items: center;
  line-height: 49px;
  box-shadow: 0 1px 1px rgba(100, 100, 100, 0.1);
  text-align: center;
  font-weight: bold;
}
.MineTop {
  width: 100%;
  height: 130px;
  background-image: linear-gradient(-225deg, #9EFBD3 0%, #57E9F2 48%, #45D4FB 100%);
  display: flex;
  border-bottom: 10px solid #e8e8e8;
}
.pic {
  width: 80px;
  height: 80px;
  margin: auto 20px;
  border-radius: 50%;
  overflow: hidden;
}
.pic img {
  width: 80px;
  height: 80px;
}
.username {
  width: 100px;
  height: 20px;
  margin-top: 35px;
  font-size: 17px;
  font-weight: bold;
  color: #3D4E81;
  
}
.details {
  width: 95px;
  height: 50px;
  margin-top: 15px;
  margin-left: 60px;
  line-height: 50px;
  font-size: 15px;
  display: flex;
  align-items: center;

}
.MineMid {
  width: 100%;
  height: 190px;
  background-color: #fff;
  border-bottom: 1px solid #e8e8e8;
}
.MineMid ul {
  width: 400px;
  display: flex;
  flex-flow: wrap;
  justify-content: center;
  overflow: hidden;
  margin-left: -12px;
  
}
.MineMid ul li {
  width: 93px;
  height: 95px;
  background-color: #fff;
  border-bottom: 1px solid #e8e8e8;
  border-right: 1px solid #e8e8e8;
  font-size: 16px;
}
.MineMid ul li img {
  margin-top: 20px;
  margin-left: 30px;
}
.MineMid ul li p {
  margin-top: 5px;
  text-align: center;
}
.MineLow {
  width: 100%;
  
}
.top {
  height: 40px;
  width: 100%;
  background-color: #e8e8e8;
  padding-left: 10px;
  line-height: 40px;
  color: #c9c9c9;
}
.list {
  width: 100%;
  height: 45px;
  background-color: #fff;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-left: 10px;
  color: #878787;
  border-bottom: 1px solid #f1f1f1;
  
}
.list img {
  margin-right: 20px;
  width: 20px;
  height: 20px;
}
.popup {
  width: 100%;
  height: 100%;
}
.popup img {
  margin-top: 100px;
  margin-left: -10px;
}
.popup h3 {
  width: 100%;
  text-align: center;
}
</style>
