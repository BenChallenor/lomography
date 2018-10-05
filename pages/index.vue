<template>

  <section class="container">
  <div>
    <b-carousel id="carousel1"
                style="text-shadow: 1px 1px 2px #333;"
                controls
                indicators
                background="black"
                :interval="1000"
                width="auto"
                >


      <b-carousel-slide v-for="(image,index) in images":key="image.id" :img-src="image.assets.large.url">
      </b-carousel-slide>
    </b-carousel>
  </div>
  </section>
</template>

<script>

import axios from 'axios'

export default {

  data() {
    return {
      images: [],
      // slide: 0,
      // sliding: null
    }
  },

  // methods: {
  //   onSlideStart (slide) {
  //     this.sliding = true
  //   },
  //   onSlideEnd (slide) {
  //     this.sliding = false
  //   }
  // },

  created() {
    axios.get('http://api.lomography.com/v1/photos/popular?api_key=73023b4ef2870abf40b6786e732625').then(images=>{
      // creates a promise then..

      // console.log(posts); to check what is returning & where to pull data
      // this.posts = posts.data
      console.log(images.data.photos);
      this.images = images.data.photos;
    });
  }
}
</script>

<style>
.b-carousel {
/* height: 300px */

}

.w-100 {
  height: 600px;
  width: auto !important;
}

.img-fluid {
  width: auto;
}

.container {
  /* margin-left: 0;
  margin-right: 0; */
  width: auto;
}

.carousel-item.active {
align-items: center;
}


</style>
