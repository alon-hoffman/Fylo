<template>
  <div class="toy-detailes-container container" v-if="toy">
    <div class="toy-details flex align-center">
      <div class="toy-info">
        <h2>{{ toy.name }}</h2>
        <h3>Price: ${{ toy.price }}</h3>
        <h3>Type: {{ toy.type }}</h3>
        <h3>{{ toyInStock }}</h3>
        <h4>The toy was created at: {{ date }}</h4>
      </div>
      <div class="img-container">
        <img v-if="toy.imgUrl" :src="toy.imgUrl" alt="toy-img" />
        <img
          v-else
          src="https://www.pulsecarshalton.co.uk/wp-content/uploads/2016/08/jk-placeholder-image.jpg"
          alt="image placeholder"
        />
      </div>
    </div>
    <div class="review-container">
      <div class="review-add flex">
        <input type="text" v-model="review" placeholder="Write your review" />
        <button @click="addReview" class="btn">Save</button>
      </div>
      <details v-if="reviews" class="review-list">
        <summary>Reviews</summary>
        <div v-for="review in reviews" :key="review._id" class="review-preview">
          <h4>By {{ review.user.username }}</h4>
          <p>{{ review.content }}</p>
        </div>
      </details>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      toy: null,
      review: '',
    };
  },
  computed: {
    toyInStock() {
      return this.toy.inStock
        ? 'Toy is in stock'
        : 'Toy is not available in stock';
    },
    date() {
      return new Date(this.toy.createdAt).toLocaleDateString();
    },
    reviews() {
      return this.$store.getters.getReviews;
      // return null
    },
  },
  created() {
    var toyId = this.$route.params.id;
    this.getToyById(toyId);
    this.getReviews(toyId);
  },
  methods: {
    async getToyById(toyId) {
      this.toy = await this.$store.dispatch({
        type: 'getToyById',
        toyId,
      });
    },
    async getReviews(toyId) {
      await this.$store.dispatch({
        type: 'getReviews',
        filterBy: { toyId },
      });
    },
    async addReview() {
      await this.$store.dispatch({
        type: 'addReview',
        toyId: this.toy._id,
        content: this.review,
      });
      this.review = '';
      this.getReviews(this.toy._id);
      // this.getToyById(this.toy._id);
    },
  },
};
</script>
