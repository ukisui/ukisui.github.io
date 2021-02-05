<template>
  <div class="bg">
    <div class="content">
      <transition name="fade" mode="out-in">
        <keep-alive>
          <gallery
            v-if="index !== null"
            :mainSrc="galleries[index].mainSrc"
            :commentTitle="galleries[index].commentTitle"
            :commentIrai="galleries[index].commentIrai"
            :commentDesign="galleries[index].commentDesign"
            :subImages="galleries[index].subImages"
            :key="index"
          />
        </keep-alive>
      </transition>

      <div v-if="index > 0" class="back-button" @click="index -= 1"></div>
      <div
        v-if="index < galleries.length - 1"
        class="forward-button"
        @click="index += 1"
      ></div>
    </div>
  </div>
</template>
<script>
import Gallery from "../components/gallery.vue";
import { galleriesTemplate } from "../assets/gallery";
export default {
  components: {
    Gallery
  },
  data() {
    return {
      index: null,
      galleries: galleriesTemplate
    };
  }
};
</script>
<style lang="scss" scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
.forward-button {
  width: 40px;
  height: 100px;
  background-image: url("/img/right.png");
  background-repeat: no-repeat;
  position: absolute;
  top: 40%;
  right: -10%;
}
.forward-button:hover {
  opacity: 0.5;
  cursor: pointer;
}
.back-button {
  width: 40px;
  height: 100px;
  background-image: url("/img/left.png");
  background-repeat: no-repeat;
  position: absolute;
  top: 40%;
  left: -10%;
}
.back-button:hover {
  opacity: 0.5;
  cursor: pointer;
}
.bg {
  background-color: #fff;
  border-radius: 40px;
  display: flex;
  justify-content: center;
}
.content {
  width: 80%;
  position: relative;
  min-height: 70vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
