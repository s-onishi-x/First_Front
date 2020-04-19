<template>
  <v-carousel
    cycle
    height="400"
    hide-delimiter-background
    show-arrows-on-hover>
    <v-carousel-item v-for="item in slides" :key="item.image">
      <v-sheet
        :color="item.color"
        height="100%">
        <v-img :src="item.image" aspect-ratio="1.7"></v-img>
      </v-sheet>
    </v-carousel-item>
  </v-carousel>
</template>

<script>
export default {
  name: "Home",
  data: () => ({
    slides: [
      {image: require("../assets/slide_image1.jpg"), color: "black"},
      {image: require("../assets/slide_image2.jpg"), color: "black"},
      {image: require("../assets/slide_image3.jpg"), color: "black"}
    ]
  })
};
</script>