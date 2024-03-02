<template>
  <a-row :gutter="32" class="gallery-container">
    <a-col :xs="24" :md="8">
      <div class="itinerary-swiper-container">
        <swiper :loop="true" :navigation="true" :modules="modules">
          <swiper-slide v-for="imgUrl in data.gallery">
            <img :src="imgUrl" alt="gallery image" />
          </swiper-slide>
        </swiper>
      </div>
    </a-col>
    <a-col :xs="24" :md="16" class="desc-container">
      <a-flex justify="space-between" vertical :style="{ height: '100%' }">
        <div>
          <a-row>
            <a-col flex="100px">
              <a-typography-title :level="3" :style="{ color: '#196d7d' }">
                {{ data.day }}
              </a-typography-title>
            </a-col>
            <a-col flex="auto">
              <a-typography-title :level="3">
                {{ data.title }}
              </a-typography-title>
            </a-col>
          </a-row>
          <a-typography-text type="secondary">
            {{ data.desc }}
          </a-typography-text>
        </div>
        <a-typography-link
          href="#"
          target="_blank"
          :style="{ color: '#307582', textDecoration: 'underline' }"
        >
          Show More
        </a-typography-link>
      </a-flex>
    </a-col>
  </a-row>
</template>

<script>
import { LeftOutlined, RightOutlined } from "@ant-design/icons-vue";
import { ref } from "vue";

import { Swiper, SwiperSlide } from "swiper/vue";
import { Navigation } from "swiper/modules";
import "swiper/css";
import "swiper/css/navigation";

export default {
  components: {
    Swiper,
    SwiperSlide,
  },
  props: {
    data: {
      type: Object,
    },
  },
  setup(props) {
    return {
      data: props.data,
      modules: [Navigation],
    };
  },
};
</script>

<style scoped>
.gallery-container {
  padding: 0 12px;
}

.desc-container {
  min-height: 0px;
}

@media (min-width: 768px) {
  .gallery-container {
    padding: 0 24px;
  }

  .desc-container {
    min-height: 160px;
  }
}

.itinerary-swiper-container {
  margin-bottom: 24px;
}

@media (min-width: 768px) {
  .itinerary-swiper-container {
    margin-bottom: 0px;
  }
}

.itinerary-swiper-container .swiper {
  width: 100%;
  max-width: 75vw;
  height: 230px;
  margin: 0;
}

.itinerary-swiper-container .swiper-slide img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 8px;
}
</style>
