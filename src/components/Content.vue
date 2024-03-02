<template>
  <a-layout-content class="container content-wrapper">
    <div class="content">
      <a-flex gap="small" align="center" justify="space-between" wrap="wrap">
        <a-breadcrumb separator=">">
          <a-breadcrumb-item>Asia</a-breadcrumb-item>
          <a-breadcrumb-item>Singapore</a-breadcrumb-item>
          <a-breadcrumb-item>Strenous Travel Style</a-breadcrumb-item>
        </a-breadcrumb>
        <a-typography-text type="secondary" :style="{ fontSize: '12px' }">
          ID: 09781021
        </a-typography-text>
      </a-flex>

      <div :style="{ padding: '16px 0' }">
        <a-typography-title :level="1">
          {{ itineraryData.title }}
        </a-typography-title>
        <a-typography-text :style="{ fontSize: '16px', fontWeight: 600 }">
          {{ itineraryData.desc }}
        </a-typography-text>
      </div>

      <a-flex align="center" gap="16" :style="{ padding: '12px 0 36px 0' }">
        <BuildOutlined :style="{ fontSize: '32px', color: '#307582' }" />
        <a-typography-text :style="{ fontSize: '32px', color: '#254d54' }">
          Itinerary
        </a-typography-text>
      </a-flex>

      <a-timeline>
        <a-timeline-item
          v-for="timeline in itineraryData.timelines"
          color="#307582"
        >
          <template #dot>
            <div :style="{ position: 'relative' }">
              <div class="dot" />
            </div>
          </template>
          <Itinerary :data="timeline" />
        </a-timeline-item>
      </a-timeline>
    </div>
  </a-layout-content>
</template>

<script setup>
import { reactive } from "vue";
import { BuildOutlined } from "@ant-design/icons-vue";
import Itinerary from "./Itinerary.vue";

const itineraryData = reactive({
  title: "Marina Bay Sands Observation",
  desc: "A great spot for R&R; order yourself a drink from the bar and get comfortable on one of the day beds that line the impressive 100-metre pool.",
  timelines: [
    {
      day: "Day 1",
      title: "See the largest indoor water fall in the world",
      desc: "Just how much mind-boggling can be pack into a 14-day holiday? Well we'll tell you. Our hot adventure pack serious punch on a journey Singapore and Malaysia.",
      gallery: [
        "/assets/gallery/1.jpg",
        "/assets/gallery/2.jpg",
        "/assets/gallery/3.jpg",
      ],
    },
    {
      day: "Day 2",
      title: "Two giant conservatories",
      desc: "Two giant conservatories rise beside Marina Bay like futuristic shells, one home to ancient olive trees, the other to a towering, tropical mountain. To the north are the Supertrees: futuris...",
      gallery: [
        "/assets/gallery/2.jpg",
        "/assets/gallery/5.jpg",
        "/assets/gallery/4.jpg",
      ],
    },
    {
      day: "Day 3",
      title: "Singapore's 21-st century botanical garden",
      desc: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas ac est diam. Duis nec aliquam diam. Proin ac augue vel tortor laoreet blandit ac tempor ipsum. ",
      gallery: [
        "/assets/gallery/3.jpg",
        "/assets/gallery/4.jpg",
        "/assets/gallery/3.jpg",
      ],
    },
  ],
});
</script>

<style>
.content-wrapper {
  background: #fff;
  border: 1px solid #eff3f4;
  border-radius: 8px;
  z-index: 2;
  margin: -250px 0 100px 0;
}

.content {
  padding: 12px;
}

@media (min-width: 768px) {
  .content-wrapper {
    margin-top: -55px;
  }

  .content {
    padding: 24px 40px;
  }
}

.dot {
  position: absolute;
  top: 97px;
  left: -8px;
  height: 16px;
  width: 16px;
  background-color: #fff;
  border: 4px solid #307582;
  border-radius: 50%;
  display: inline-block;
}

/* override ant timeline tail */
.ant-timeline-item-tail {
  margin-top: 97px;
}
</style>
