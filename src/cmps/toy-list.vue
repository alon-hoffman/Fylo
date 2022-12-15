<template>
  <section class="toy-list-container">
    <!-- <router-link to="toy/edit/" class="add-new-toy-btn btn">add</router-link> -->
    <button @click="toAddToy()">Add Toy</button>
    <!-- <ul class="toy-list clean-list flex space-between wrap"> -->
    <ul class="toy-list clean-list toy-list-layout">
      <toy-preview v-for="toy in toys" :key="toy._id" :toy="toy" />
    </ul>
  </section>
</template>

<script>
  import toyPreview from './toy-preview.vue';
  export default {
    props: {
      toys: Array,
    },
    components: {
      toyPreview,
    },
    methods: {
      toAddToy() {
        this.$router.push('/toy/edit');
      },
    },
  };
</script>
<style scoped>
  .toy-list-container a {
    margin-bottom: 10px;
    display: inline-block;
  }
</style>
