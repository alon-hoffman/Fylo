<template>
  <section class="about-page-container">
    <h1>About Us</h1>
    <section class="branch-container flex column align-center">
      <!-- <map-cmp :branches="branches" :currBranch="currBranch" />
      <h2>Owr Branches</h2>
      <ul class="branch-list flex space-between clean-list">
        <li
          class="branch-preview"
          @click="currBranch = b"
          v-for="(b, idx) in branches"
          :key="idx"
        >
          {{ b.city }}
        </li>
      </ul> -->
    </section>
  </section>
</template>

<script>
  // import mapCmp from '../cmps/map.cmp.vue';
  export default {
    data() {
      return {
        branches: [
          {city: 'Petach Tikva', position: {lat: 32.09573, lng: 34.881865}},
          {city: 'Tel Aviv', position: {lat: 32.08704, lng: 34.775293}},
          {city: 'Netanya', position: {lat: 32.290295, lng: 34.861591}},
        ],
        currBranch: null,
      };
    },
    components: {
      // mapCmp,
    },
  };
</script>
