<template>
  <section class="toy-app-container container">
    <toy-filter />
    <toy-list :toys="toys" />
  </section>
</template>

<script>
import toyList from '@/cmps/toy-list.vue';
import toyFilter from '@/cmps/toy-filter.vue';

export default {
  created() {
    this.$store.dispatch('loadToys');
  },
  computed: {
    toys() {
      return this.$store.getters.getToys;
    },
  },
  components: {
    toyList,
    toyFilter,
  },
};
</script>
