<template>
  <div class="detailNavbar">
    <div class="back" @click="backClick">
      <img src="~assets/img/backwrite.png" alt="" />
    </div>
    <div class="title">
      <div class="box1" v-if="!changeContext">歌单</div>
      <!-- <div class="box3" v-else="changeContext">{{ name }}</div> -->
      <div class="box2">{{ description }}</div>
    </div>

    <div class="search" @click="searchClick">
      <img src="~assets/img/navbar/search1.png" alt="" />
    </div>
    <div class="sort" @click="showPopup">
      <img src="~assets/img/sort.png" alt="" />
    </div>

  </div>
</template>

<script>
import { Popup } from "vant";
export default {
  name: "DetailNavbar",
  components: {
    [Popup.name]: Popup,
  },
  props: ["description", "changeContext", "name"],
  methods: {
    backClick() {
      this.$router.back();
    },
    searchClick() {
      this.$router.push("/search");
    },
    showPopup() {
      this.show = true;
      this.$emit('event1', this.show)
    },
  },
  data() {
    return {
      show: false,
    };
  },
};
</script>

<style scoped>
.detailNavbar {
  position: relative;
  top: 0;
  z-index: 900;
  background-color: #64d09c;
  height: 50px;
  line-height: 50px;
  width: 100%;
  display: flex;
  text-align: center;
  color: white;
  opacity: 0.9;
}
.back {
  padding-top: 6px;
  flex: 1;
}
.back img {
  width: 24px;
  height: 24px;
}
.title {
  height: 50px;
  line-height: 25px;
  flex: 4;
  display: flex;
  text-align: left;
  flex-direction: column;
  justify-content: space-around;
  min-width: 0;
}
.title .box1 {
  flex: 1;
  font-size: 18px;
  margin: 5px 0 -7px 0;
}
.title .box2 {
  flex: 1;
  font-size: 12px;
  letter-spacing: 0.4px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  margin-top: 5px;
  
}
.title .box3 {
  flex: 1;
  font-size: 15px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  opacity: 0.8;
  padding-top: 5px;
}

.search {
  flex: 1;
}
.search img {
  width: 7.222vw;
  vertical-align: middle;
}
.sort {
  padding-top: 4px;
  flex: 1;
}
.sortname {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
.sortPopup div {
  position: relative;
  text-align: left;
  padding-left: 20px;
}
.sortPopup div img {
  width: 24px;
  height: 24px;
}
.sortPopup div span {
  position: absolute;
  top: -6px;

  padding-left: 10px;
  font-size: 16px;
}
</style>