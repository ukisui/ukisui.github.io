<template>
  <div class="gallery">
    <div class="banner-img">
      <img :src="mainSrc" alt="" />
    </div>
    <div class="comment-body">
      <div class="banner-title">
        {{ commentTitle }}
      </div>
      <div class="banner-comment">
        <div class="banner-comment-irai">
          <p v-for="comment in commentIrai" :key="comment">
            {{ comment }}
          </p>
        </div>
        <div class="banner-comment-design">
          <p v-for="design in commentDesign" :key="design">
            {{ design }}
          </p>
        </div>
      </div>
      <div class="banner-sub">
        <div v-for="sub in subImages" :key="sub.src">
          <div class="banner-sub-text">
            {{ sub.text }}
          </div>
          <div class="banner-sub-img">
            <img :src="sub.src" alt="" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    mainSrc: {
      type: String
    },
    subImages: {
      type: Array
    },
    commentTitle: {
      type: String
    },
    commentIrai: {
      type: Array
    },
    commentDesign: {
      type: Array
    }
  }
};
</script>
<style lang="scss" scoped>
.gallery {
  font-family: YuGothic, "Yu Gothic", "Hiragino Kaku Gothic ProN",
    "ヒラギノ角ゴ ProN W3", "Arial", "メイリオ", Meiryo, sans-serif;
  display: flex;
  flex-direction: row;
  .banner-img {
    // width: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    // background-color: #555555;
    max-height: 80%;
    img {
      
    }
  }
  .banner-sub {
    display: flex;
    flex-direction: row;
  }
  .banner-sub-img {
    width: 200px;
    padding-right: 10px;
  }
  .banner-sub-text {
    font-size: 13px;
    text-align: left;
    padding-right: 10px;
  }
  .comment-body {
    // width: 50%;
    display: flex;
    flex-direction: column;
    padding: 50px;
    padding-right: 0;
    p {
      margin-bottom: 0;
    }
  }
  .banner-title {
    font-size: 20px;
    padding-bottom: 30px;
  }
  .banner-comment {
    font-size: 14px;
    // width: 60%;
    padding-bottom: 30px;
    text-align: left;
  }
  .banner-comment-irai {
    padding-bottom: 20px;
  }
  //   .banner-comment-design{

  //   }
}
</style>
