<template>
  <div>
    <section v-if="!isMobile" class="full-section_pad ct-services">
      <slot />  
      <carousel :autoplay="true" :nav="false" :center="false" 
        :responsive="{0:{items:1,nav:false},600:{items:2},1200:{items:3}}" class="reviews">
          <Review 
            v-for="(review) in reviews"
            :key="review.name"
            :name="review.name"
            :subtitle="review.subtitle"
          >
            <div v-for="(text, index) in review.texts" 
              :key="`text-${index + 1}`"
            >
              <p class="review__text" >{{ text }}</p>
            </div>
          </Review>
      </carousel>     
    </section>
    <section v-else-if="isMobile" class="full-section ct-services default-bg">
      <MobileHeader :title="`Отзывы`" />
      <carousel :autoplay="true" :nav="false" :center="false" 
        :responsive="{0:{items:1,nav:false},600:{items:2},1200:{items:3}}" class="reviews">
          <Review 
            v-for="(review) in reviews"
            :key="review.name"
            :name="review.name"
            :subtitle="review.subtitle"
          >
            <div v-for="(text, index) in review.texts" 
              :key="`text-${index + 1}`"
            >
              <p class="review__text" >{{ text }}</p>
            </div>
          </Review>
      </carousel>  
    </section>
  </div>
</template>

<script>
import carousel from 'vue-owl-carousel';
import MobileHeader from '../components/MobileHeader.vue'
import Review from '../components/reviews/Review.vue';

export default {
  components: { Review, carousel, MobileHeader },
  data() {
    return {
      reviews: require('../assets/json/reviews.json')
    }
  }
}
</script>

<style lang="scss">
.owl-theme .owl-nav.disabled + .owl-dots {
    margin-top: 40px !important;
}
.owl-theme .owl-dots .owl-dot span {
  width: 20px !important;
  height: 20px !important;
}
.owl-theme .owl-dots .owl-dot.active span {
  background: #fff !important;
}


.reviews {
  max-width: 1235px;
  width: 100%;
  margin: 0 auto;
}
.review {
  background: #fff;
  border-radius: 5px;
  border-top: 15px solid #EF3B39;
  max-width: 400px;
  width: 100%;
  height: 600px;
  color: #545454;
  font-weight: normal;
  padding: 30px 30px;
  margin: 0 10px;

  &__name {
    text-align: center;
    font-size: 30px;
    font-weight: 900; 
    margin-bottom: 10px;   
  }

  &__subtitle {
    text-align: center;
    font-size: 18px;  
    padding-bottom: 10px;
    margin-bottom: 10px;
    border-bottom: 1px dashed #D3D3D3;
  }

  &__text {
    font-size: 14px;
    text-align: justify;
  }
}

@media (max-width: 1200px) {
  .reviews {
    max-width: 820px;
  }
  .review {
    padding: 20px 20px;
    margin: 0 auto;
    height: 500px;
    &__name, &__subtitle {
      margin-bottom: 5px;
    }
  }
}

@media (max-width: 767px) {
  .owl-theme .owl-dots .owl-dot span {
    width: 15px !important;
    height: 15px !important;
  }
  .owl-theme .owl-nav.disabled + .owl-dots {
    margin-top: 25px !important;
    padding-bottom: 30px !important;
  }
  .reviews {
    padding: 0 15px;
  }
  .review {
    height: 560px;
  }
}
</style>