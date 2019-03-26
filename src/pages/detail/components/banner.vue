<template>
  <div>
    <div
      class="banner"
      @click="handleBannerClick"
    >
      <img
        class="banner-img"
        :src="bannerImg"
        alt=""
      >
      <div class="banner-info">
        <p class="banner-title">{{sightName}}</p>
        <div class="banner-number">
          <span class="iconfont banner-icon">&#xe692;</span>
          {{this.bannerImgs.length}}
        </div>
      </div>
    </div>
    <fade-animation>
      <common-gallary
        :imgs="bannerImgs"
        v-show="showGallary"
        @close="handelGallaryClose"
      ></common-gallary>
    </fade-animation>
  </div>
</template>
<script>
import CommonGallary from "common/gallary/gallary";
import FadeAnimation from "common/fade/Fade";
export default {
  name: "detailBanner",
  props: {
    sightName: String,
    bannerImg: String,
    bannerImgs: Array
  },
  data() {
    return {
      showGallary: false
    };
  },
  components: {
    CommonGallary,
    FadeAnimation
  },
  methods: {
    handleBannerClick() {
      this.showGallary = true;
    },
    handelGallaryClose() {
      this.showGallary = false;
    }
  }
};
</script>
<style lang="stylus" scoped>
.banner
  overflow: hidden
  position: relative
  height: 0
  padding-bottom: 55%
  color: #fff
  .banner-img
    width: 100%
  .banner-info
    position: absolute
    left: 0
    right: 0
    bottom: 0
    line-height: 0.6rem
    display: flex
    background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8))
    .banner-title
      flex: 1
      font-size: 0.32rem
      padding: 0 0.2rem
    .banner-number
      height: 0.32rem
      margin-top: 0.14rem
      padding: 0 0.4rem
      line-height: 0.32rem
      border-radius: 0.2rem
      background: rgba(0, 0, 0, 0.8)
      font-size: 0.24rem
      .banner-icon
        font-size: 0.24rem
</style>


