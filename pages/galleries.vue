<template>
  <div>
    <gallery
      :mainSrc="galleries[index].mainSrc"
      :commentTitle="galleries[index].commentTitle"
      :commentIrai="galleries[index].commentIrai"
      :commentDesign="galleries[index].commentDesign"
      :subImages="galleries[index].subImages"
    ></gallery>
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
      index: 0,
      galleries: galleriesTemplate
    };
  }
};
</script>
