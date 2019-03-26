<template>
  <div>
    <detail-banner
      :sightName="sightName"
      :bannerImg="bannerImg"
      :bannerImgs="gallaryImgs"
    ></detail-banner>
    <detail-header></detail-header>
    <div class="content">
      <detail-list :list="list"></detail-list>
    </div>
  </div>
</template>
<script>
import detailBanner from "./components/banner";
import detailHeader from "./components/Header";
import detailList from "./components/list";
import axios from "axios";
export default {
  name: "Detail",
  components: {
    detailBanner,
    detailHeader,
    detailList
  },

  data() {
    return {
      sightName: "",
      bannerImg: "",
      gallaryImgs: [],
      list: []
    };
  },
  methods: {
    getDeatilInfo() {
      // axios.get("/api/detail.json?id=" + this.$route.params.id);
      axios
        .get("/api/detail.json", {
          params: {
            id: this.$route.params.id
          }
        })
        .then(this.handleGetDataSucc);
    },
    handleGetDataSucc(res) {
      res = res.data;
      if (res.ret && res.data) {
        const data = res.data;
        this.sightName = data.sightName;
        this.bannerImg = data.bannerImg;
        this.gallaryImgs = data.gallaryImgs;
        this.list = data.categoryList;
      }
    }
  },
  mounted() {
    this.getDeatilInfo();
  }
};
</script>
<style lang="stylus" scoped>
.content
  height: 50rem
</style>


