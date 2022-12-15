<template>
  <section class="dashboard-page-container flex">
    <h1>Dashboard</h1>
    <!-- <pie-chart
      v-if="dataReady"
      class="pie-chart"
      :inStockTypes="inStockTypesMap"
    /> -->
    <!-- <bar-chart class="bar-chart" :pricePerType="pricePerType" /> -->
  </section>
</template>

<script>
  // import pieChart from '../cmps/charts/pie-chart.cmp.vue';
  // import barChart from '../cmps/charts/bar-chart.cmp.vue';
  export default {
    data() {
      return {
        dataReady: false,
      };
    },
    computed: {
      toys() {
        return this.$store.getters.getToys;
      },
      inStockTypesMap() {
        return this.toys?.reduce((data, toy) => {
          if (!data[toy.type]) data[toy.type] = 0;
          if (toy.inStock) data[toy.type]++;
          return data;
        }, {});
      },
      // pricePerType() {
      //   return this.toys?.reduce(
      //     (data, toy) => {
      //       console.log(data);
      //       if(toy.type !== 'Funny') {
      //         console.log('DATAAAAA', data);
      //         return data
      //          }
      //       if (parseInt(toy.price) <= 10) data['0-10']++;
      //       else if (parseInt(toy.price) <= 50) data['11-50']++;
      //       else if (parseInt(toy.price) <= 100)data['51-100']++
      //       else if (parseInt(toy.price) <= 200) data['100-200']++
      //       else data['200+']++
      //       return data;
      //     },
      //     { '0-10': 0, '11-50': 0, '51-100': 0, '100-200': 0, '200+': 0 }
      //   );
      // },
    },
    async created() {
      try {
        await this.$store.dispatch('loadToys');
        this.dataReady = true;
      } catch (err) {
        console.log("Couldn't get toys", err);
      }
    },
    components: {
      // pieChart,
      // barChart,
    },
  };
</script>
