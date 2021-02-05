<template>
  <div id="top" class="container">
    <div>
      <transition name="move">
        <div v-if="show" class="portfolio">
          portfolio
        </div>
      </transition>
      <transition name="fade">
        <div v-if="show" class="top-img"></div>
      </transition>
      <transition name="move">
        <div v-if="show" class="menu-header">
          <div class="menu-about" @click="scrollAbout">
            about
          </div>
          <div class="menu-gallery" @click="scrollGallery">
            gallery
          </div>
        </div>
      </transition>
      <transition name="move-hana">
        <div v-if="show" class="bg-hana"></div
      ></transition>
      <transition name="move-hana">
        <div v-if="show" class="bg-hana2"></div
      ></transition>
      <transition name="move-hana">
        <div v-if="show" class="bg-hana3"></div
      ></transition>
      <transition name="move-hana">
        <div v-if="show" class="bg-hana4"></div
      ></transition>
      <transition name="move-hana">
        <div v-if="show" class="bg-hana5"></div
      ></transition>
      <transition name="move-hana">
        <div v-if="show" class="bg-hana6"></div
      ></transition>
      <transition name="move-hana">
        <div v-if="show" class="bg-hana7"></div
      ></transition>
      <transition name="move-hana">
        <div v-if="show" class="bg-hana8"></div
      ></transition>
      <transition name="move-hana">
        <div v-if="show" class="bg-hana9"></div
      ></transition>
      <transition name="move">
        <div v-if="show" class="scroll-button-wrapper" @click="scrollTop">
          <svg fill="none" stroke="white" class="scroll-button">
            <use xlink:href="/svg/menu1.svg#item" />
          </svg>
          <div class="scroll-message">
            <p>u</p>
            <p>k</p>
            <p>i</p>
            <p>s</p>
            <p>u</p>
            <p>i</p>
          </div>
        </div>
      </transition>
      <transition name="move">
        <div v-if="show" ref="about" class="about">
          <div class="title">
            About
          </div>
          <div class="about-body">
            <div class="profile-body">
              <div class="profilename-body">
                <div class="profile-icon">
                  <img src="/img/profile-icon.png" alt="" />
                </div>
                <div class="profile-name temp">
                  宇機 すい
                </div>
                <div class="profilename-rubi">
                  Uki Sui
                </div>
              </div>
              <div class="profile-main">
                <p>1993年生まれ。</p>
                <p>
                  デザイン科高校卒業後、東京の美術館で販売の傍らPOP・チラシ制作を行う。
                </p>
                <p>
                  現在はクラウドワークスにて、主にロゴ・バナー・チラシ制作をメインに活動中。
                </p>
                <p>趣味は応援上映。</p>
              </div>
            </div>
            <div class="line"></div>
            <div class="skill">
              <div class="skill-title temp">
                Skill
              </div>
              <div class="skills-wrapper">
                <div v-for="(skill, i) in skills" :key="i" class="skills">
                  <div class="skill-body">
                    <div class="skill-icon">
                      <img :src="skill.iconSrc" alt="" />
                    </div>
                    <div class="skillhyouka-body">
                      <div class="skill-hoshi">
                        <img :src="skill.rateSrc" alt="" />
                      </div>
                      <div class="skill-name">
                        {{ skill.name }}
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </transition>
      <transition name="move">
        <div v-if="show" ref="gallery" class="gallery">
          <div class="title">
            Gallery
          </div>

          <div class="gallerys-wrapper">
            <div
              v-for="(gallery, i) in gallerys"
              :key="i"
              class="gallerys"
              @click="showModal(i)"
            >
              <div class="gallery-body">
                <div class="g-image-wrapper">
                  <div class="g-image">
                    <div class="g-bg">
                      <img :src="gallery.imgSrc" alt="" />
                      <div class="g-title">
                        {{ gallery.title }}
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </transition>
      <transition name="move">
        <div v-if="show" class="footer">
          <div class="footer-main">
            ©︎2021 ukisui
          </div>
        </div>
      </transition>
      <div :class="['modal', modalIndex === null ? null : 'is-active']">
        <div class="modal-background" @click="showModal(null)"></div>
        <div class="modal-content">
          <galleries ref="galleries"></galleries>
        </div>
        <button
          class="modal-close is-large"
          aria-label="close"
          @click="showModal(null)"
        ></button>
      </div>
    </div>
  </div>
</template>

<script>
import Galleries from "../components/galleries.vue";
export default {
  components: {
    Galleries
  },
  data() {
    return {
      gallerys: [
        {
          title: "プライベートサロンのロゴ作成",
          imgSrc: "/img/namioto-icon.png"
        },
        {
          title: "イタリアンレストラン TAKEOUTメニュー",
          imgSrc: "/img/takeout-icon.png"
        },
        {
          title: "ファッションサイト バナー",
          imgSrc: "/img/fashion-icon.png"
        },

        {
          title: "不動産チラシ(モノクロ)",
          imgSrc: "/img/rbm-icon.png"
        },
        {
          title: "SNSヘッダー",
          imgSrc: "/img/nsbs-icon.png"
        },
        {
          title: "ミスコン インスタ用バナー",
          imgSrc: "/img/oruchan-icon.png"
        },
        {
          title: "レトロゲーム風バナー広告",
          imgSrc: "/img/tec-icon.png"
        },
        {
          title: "不用品回収バナー",
          imgSrc: "/img/kataduke-icon.png"
        },
        {
          title: "ゴルフシミュレーション&BARの割引チケット",
          imgSrc: "/img/golf-icon.png"
        },
        {
          title: "アイクリームLPへのインスタ用誘導バナー",
          imgSrc: "/img/cream-icon.png"
        },
        {
          title: "その他バナー例",
          imgSrc: "/img/oil-icon.png"
        }
      ],
      skills: [
        {
          name: "illusrator",
          rateSrc: "/img/hoshi5.png",
          iconSrc: "/img/ill-icon.png"
        },
        {
          name: "photoshop",
          rateSrc: "/img/hoshi3.png",
          iconSrc: "/img/ps-icon.png"
        },
        {
          name: "XD",
          rateSrc: "/img/hoshi3.png",
          iconSrc: "/img/xd-icon.png"
        },
        {
          name: "CLIP STUDIO PAINT",
          rateSrc: "/img/hoshi5.png",
          iconSrc: "/img/clip-icon.png"
        },
        {
          name: "HTML",
          rateSrc: "/img/hoshi3.png",
          iconSrc: "/img/html-icon.png"
        },
        {
          name: "CSS",
          rateSrc: "/img/hoshi3.png",
          iconSrc: "/img/css-icon.png"
        },
        {
          name: "Vue.js",
          rateSrc: "/img/hoshi2.png",
          iconSrc: "/img/vue-icon.png"
        },
        {
          name: "Nuxt.js",
          rateSrc: "/img/hoshi2.png",
          iconSrc: "/img/nuxt-icon.png"
        }
      ],
      modalIndex: null,
      show: false
    };
  },
  mounted() {
    this.show = true;
  },

  methods: {
    scrollTop() {
      window.scrollTo({
        top: 0,
        behavior: "smooth"
      });
    },
    scrollAbout() {
      window.scrollTo({
        top: this.$refs.about.offsetTop - 100,
        behavior: "smooth"
      });
    },
    scrollGallery() {
      window.scrollTo({
        top: this.$refs.gallery.offsetTop - 50,
        behavior: "smooth"
      });
    },
    showModal(i) {
      this.$refs.galleries.$data.index = i;
      this.modalIndex = i;
    }
  }
};
</script>

<style lang="scss" scoped>
.profile-icon {
  width: 70px;
  height: 70px;
  // margin-left: 80px;
  padding-bottom: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.portfolio {
  font-family: YuGothic, "Yu Gothic", "Hiragino Kaku Gothic ProN",
    "ヒラギノ角ゴ ProN W3", "Arial", "メイリオ", Meiryo, sans-serif;
  font-size: 15px;
  color: #ffffff;
  letter-spacing: 15px;
  padding: 20px;
}
.menu-header {
  position: absolute;
  font-family: YuGothic, "Yu Gothic", "Hiragino Kaku Gothic ProN",
    "ヒラギノ角ゴ ProN W3", "Arial", "メイリオ", Meiryo, sans-serif;
  font-size: 15px;
  color: #35495e;
  letter-spacing: 10px;
  display: flex;
  flex-direction: column;
  padding: 50px;
  top: 0;
  padding-top: 10%;
  width: 75%;
}
.menu-about {
  z-index: 1;
  cursor: pointer;
  text-align: left;
  margin-bottom: 50px;
  width: 10%;
}
.menu-about:hover {
  color: #fff;
}
.menu-gallery {
  cursor: pointer;
  z-index: 1;
  text-align: left;
  width: 10%;
}
.menu-gallery:hover {
  color: #fff;
}
.bg-hana {
  width: 120px;
  height: 190px;
  background-image: url("/img/hana1.png");
  background-repeat: no-repeat;
  position: absolute;
  top: 2%;
  left: 5%;
  background-size: contain;
}
.bg-hana2 {
  width: 120px;
  height: 190px;
  background-image: url("/img/hana2.png");
  background-repeat: no-repeat;
  position: absolute;
  top: 13%;
  left: -5%;
  background-size: contain;
}
.bg-hana3 {
  width: 200px;
  height: 190px;
  background-image: url("/img/hana3.png");
  background-repeat: no-repeat;
  position: absolute;
  top: 20%;
  left: 90%;
  background-size: contain;
}
.bg-hana4 {
  width: 120px;
  height: 190px;
  background-image: url("/img/hana4.png");
  background-repeat: no-repeat;
  position: absolute;
  top: 1%;
  left: 90%;
  background-size: contain;
}
.bg-hana6 {
  width: 120px;
  height: 190px;
  background-image: url("/img/hana6.png");
  background-repeat: no-repeat;
  position: absolute;
  top: 90%;
  left: 10%;
  background-size: contain;
}
.bg-hana7 {
  width: 120px;
  height: 190px;
  background-image: url("/img/hana7.png");
  background-repeat: no-repeat;
  position: absolute;
  top: 88%;
  left: 90%;
  background-size: contain;
}
.bg-hana8 {
  width: 200px;
  height: 190px;
  background-image: url("/img/hana3.png");
  background-repeat: no-repeat;
  position: absolute;
  top: 80%;
  left: -3%;
  background-size: contain;
}
.bg-hana9 {
  width: 120px;
  height: 190px;
  background-image: url("/img/hana4.png");
  background-repeat: no-repeat;
  position: absolute;
  top: 80%;
  left: 95%;
  background-size: contain;
}
.bg-hana5 {
  width: 120px;
  height: 190px;
  background-image: url("/img/hana5.png");
  background-repeat: no-repeat;
  position: absolute;
  top: 92%;
  left: 65%;
  background-size: contain;
  transform: rotate(-100deg);
}
.modal-content {
  width: 80%;
}
.menu-button-wrapper:hover {
  color: #000;
  background-color: #35495e;
}
.menu-button {
  width: 155px;
  height: 140px;
}
.menu-button-wrapper {
  position: fixed;
  left: 5%;
  top: 13%;
}
.scroll-button-wrapper:hover {
  opacity: 0.5;
}
.scroll-message {
  position: absolute;
  top: 100px;
  left: 50px;
  color: #fff;
  font-family: "klee", sans-serif;
}
.scroll-button-wrapper {
  position: fixed;
  right: 5%;
  top: 19%;
}
.scroll-button {
  width: 154px;
  height: 252px;
  cursor: pointer;
}
.top-img {
  padding-top: 48%;
  width: 75%;
  position: relative;
  background-image: url("/img/header0.png");
  background-repeat: no-repeat;
  background-size: 100%;
  background-position: 0 0;
}
.line {
  width: 1px;
  background-color: #35495e;
  transform: scaleY(1.2);
}
.footer-main {
  padding-bottom: 50px;
  font-family: YuGothic, "Yu Gothic", "Hiragino Kaku Gothic ProN",
    "ヒラギノ角ゴ ProN W3", "Arial", "メイリオ", Meiryo, sans-serif;
  font-size: 12px;
  letter-spacing: 5px;
  color: #ffffff;
}
.footer {
  background-color: inherit;
}
.g-image-wrapper {
  display: flex;
}
.g-image {
  display: flex;
  flex-direction: column;
  img:hover {
    opacity: 0.5;
    cursor: pointer;
  }
}
.g-bg {
  width: 100%;
  height: 100%;
}
.g-bg:hover {
  background-color: rgba(255, 255, 255, 0.3);
  color: #cccccc;
  cursor: pointer;
}
.g-title {
  font-family: YuGothic, "Yu Gothic", "Hiragino Kaku Gothic ProN",
    "ヒラギノ角ゴ ProN W3", "Arial", "メイリオ", Meiryo, sans-serif;
  font-size: 10px;
}
.gallery-body {
  vedisplay: flex;
  justify-content: space-between;
  flex-direction: column;
  /* align-items: center; */
  /* text-align: center; */
  width: 100%;
  height: 100%;
}
.gallerys-wrapper {
  display: flex;
  flex-wrap: wrap;
}
.gallerys {
  width: 33%;
  padding: 10px;
}
.gallery {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 60%;
  padding-bottom: 100px;
}
.g-image img {
  width: 100%;
}
.skills-wrapper {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  width: 70%;
}
.skills {
  width: 50%;
}
.skill {
  width: 50%;
  padding-left: 120px;
  padding-top: 10px;
}
.skillhyouka-body {
  display: flex;
  /* justify-content: center; */
  flex-direction: column;
  /* align-items: center; */
  text-align: left;
}
.skill-title {
  padding-bottom: 30px;
}
.skill-body {
  display: flex;
  /* justify-content: center; */
  flex-direction: row;
  /* align-items: center; */
  text-align: left;
}
.skill-name {
  font-family: YuGothic, "Yu Gothic", "Hiragino Kaku Gothic ProN",
    "ヒラギノ角ゴ ProN W3", "Arial", "メイリオ", Meiryo, sans-serif;
  font-size: 12px;
  color: #000000;
  padding-bottom: 10px;
}
.profile-main {
  font-family: YuGothic, "Yu Gothic", "Hiragino Kaku Gothic ProN",
    "ヒラギノ角ゴ ProN W3", "Arial", "メイリオ", Meiryo, sans-serif;
  font-size: 15px;
  color: #000000;
  letter-spacing: 1px;
  text-align: left;
  width: 75%;
  padding-left: 10px;
}
.profilename-rubi {
  font-family: YuGothic, "Yu Gothic", "Hiragino Kaku Gothic ProN",
    "ヒラギノ角ゴ ProN W3", "Arial", "メイリオ", Meiryo, sans-serif;
  /* display: block; */
  font-size: 14px;
  color: #a2a1a1;
  letter-spacing: 1px;
  display: flex;
  flex-direction: column-reverse;
  padding-bottom: 10px;
}
.profilename-body {
  display: flex;
  justify-content: left;
  flex-direction: row;
  align-items: center;
  // text-align: left;
  padding-bottom: 30px;
}
.profile-name {
  text-align: left;
  padding-right: 10px;
  padding-left: 10px;
  padding-bottom: 10px;
}
.profile-body {
  display: flex;
  /* justify-content: center; */
  flex-direction: column;
  /* align-items: center; */
  text-align: left;
  width: 50%;
  /* padding-right: 50px; */
  padding-left: 135px;
  padding-top: 20px;
}
.about {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.about-body {
  display: flex;
  justify-content: center;
  flex-direction: row;
  /* align-items: center; */
  text-align: center;
  width: 80%;
  padding-bottom: 80px;
}
.skill-icon {
  width: 30px;
  height: 30px;
}
.skill-icon img {
  width: 100%;
}
.skill-hoshi {
  width: 70px;
  /* height: 15px; */
}
.skill-hoshi img {
  width: 100%;
}

.temp {
  font-family: YuGothic, "Yu Gothic", "Hiragino Kaku Gothic ProN",
    "ヒラギノ角ゴ ProN W3", "Arial", "メイリオ", Meiryo, sans-serif;
  font-size: 20px;
  color: #000000;
  /* letter-spacing: 1px; */
  text-align: left;
}
/* .top-image {
  width: 80%;
  padding: 50px;
} */
.container > div {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  /* justify-content: center; */
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Roboto Slab", sans-serif;
  /* font-family: YuGothic, "Yu Gothic", "Hiragino Kaku Gothic ProN",
    "ヒラギノ角ゴ ProN W3", "Arial", "メイリオ", Meiryo, sans-serif; */
  display: block;
  font-size: 20px;
  color: #35495e;
  letter-spacing: 10px;
  padding-bottom: 50px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 1s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
.move-enter-active,
.move-leave-active {
  transition: opacity 1s, transform 1s;
  transition-delay: 1.8s;
}
.move-enter, .move-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: translate(20px, 0);
}
.move-hana-enter-active,
.move-hana-leave-active {
  transition: opacity 1s;
  transition-delay: 1s;
}
.move-hana-enter, .move-hana-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
// .bg-hana {
//   transition-delay: 2s;
// }
</style>
