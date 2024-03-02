<template>
  <div :style="{ position: 'relative', height: '500px' }">
    <div class="play-btn-wrapper" @click="videoDialogVisible = true">
      <div class="play-btn" />
    </div>

    <div id="banner-swiper-container">
      <swiper
        :slidesPerView="'auto'"
        :centeredSlides="true"
        :spaceBetween="16"
        :loop="true"
        :navigation="true"
        :modules="modules"
        @swiper="setSwiperRef"
      >
        <swiper-slide v-for="imgUrl in galleryImages">
          <img :src="imgUrl" alt="gallery image" />
        </swiper-slide>
      </swiper>
    </div>
  </div>

  <a-modal
    v-model:open="videoDialogVisible"
    title=""
    centered
    width="1000px"
    :closable="false"
    :footer="null"
  >
    <iframe
      width="100%"
      height="456px"
      style="min-height: 300px"
      src="https://www.youtube.com/embed/u33D9BhT6NA"
      title="Marina Bay Sands Hotel Singapore: full tour (spectacular rooftop pool)"
      frameborder="0"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
      allowfullscreen
    ></iframe>
  </a-modal>
</template>

<script>
import { ref } from "vue";
import { PlayCircleFilled } from "@ant-design/icons-vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import { Navigation } from "swiper/modules";
import "swiper/css";
import "swiper/css/navigation";

export default {
  components: {
    Swiper,
    SwiperSlide,
  },
  setup() {
    let swiperRef = null;
    const videoDialogVisible = ref(false);

    const setSwiperRef = (swiper) => {
      swiperRef = swiper;
      swiperRef.slideTo(3, 0);
    };

    return {
      galleryImages: [
        "/assets/gallery/2.jpg",
        "/assets/gallery/1.jpg",
        "/assets/gallery/3.jpg",
        "/assets/gallery/4.jpg",
        "/assets/gallery/5.jpg",
      ],
      swiperRef: null,
      setSwiperRef,
      videoDialogVisible,
      modules: [Navigation],
    };
  },
};
</script>

<style>
#banner-swiper-container .swiper {
  width: 100%;
  height: 250px;
}

@media (min-width: 768px) {
  #banner-swiper-container .swiper {
    min-height: 500px;
  }
}

#banner-swiper-container .swiper-slide {
  text-align: center;
  font-size: 18px;
  background: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
}

#banner-swiper-container .swiper-slide img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

#banner-swiper-container .swiper-slide {
  width: 10%;
}

#banner-swiper-container .swiper-slide:nth-child(2n) {
  width: 80%;
}

#banner-swiper-container .swiper-slide:nth-child(3n) {
  width: 10%;
}

#banner-swiper-container .swiper-button-next,
#banner-swiper-container .swiper-button-prev {
  padding: 8px;
  width: 24px;
  height: 24px;
  margin-top: 0;
  background-color: #fff;
  border-radius: 50%;
}

#banner-swiper-container .swiper-button-next::after,
#banner-swiper-container .swiper-button-prev::after {
  color: #111;
  font-size: 12px;
}

#banner-swiper-container .swiper-button-next {
  transform: translate(50%, -50%);
  right: 12%;
}

#banner-swiper-container .swiper-button-prev {
  transform: translate(-50%, -50%);
  left: 12%;
}

.play-btn-wrapper {
  position: absolute;
  top: 85px;
  left: calc(50% - 40px);
  z-index: 3;
}

.play-btn {
  width: 80px;
  height: 80px;
  background: radial-gradient(rgba(255, 0, 0, 1) 50%, rgba(255, 0, 0, 0.4) 32%);
  border-radius: 50%;
  position: relative;
  display: block;
}

.play-btn:hover {
  cursor: pointer;
}

.play-btn::after {
  content: "";
  position: absolute;
  left: 50%;
  top: 50%;
  -webkit-transform: translateX(-40%) translateY(-50%);
  transform: translateX(-40%) translateY(-50%);
  transform-origin: center center;
  width: 0;
  height: 0;
  border-top: 15px solid transparent;
  border-bottom: 15px solid transparent;
  border-left: 25px solid #fff;
  z-index: 100;
}

@media (min-width: 768px) {
  .play-btn-wrapper {
    top: 200px;
    left: calc(50% - 50px);
  }

  .play-btn {
    width: 100px;
    height: 100px;
  }
}
</style>
