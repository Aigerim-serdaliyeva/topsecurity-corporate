<template>
  <div>
    <Review 
      v-for="(review, index) in reviews"
      :key="`review-${index + 1}`"
      :name="review.name"
      :subtitle="review.subtitle"
    >
      <div v-for="(text, index) in review.texts" 
        :key="`text-${index + 1}`"
      >
        <p >{{ text }}</p>
      </div>
    </Review>
  </div>
</template>

<script>
import Review from '../reviews/Review.vue'
export default {
  components: { Review },
  data() {
    return {
      reviews: require('../../assets/json/reviews.json')
    }
  }
}
</script>