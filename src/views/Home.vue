<template>
  <main v-if="!loading">
    <DataTitle :text="title" :dataDate="dataDate" />
  </main>
  <main class="flex flex-col align-center justify-center text-center" v-else>
    <div class="text-gray-500 text-3l mt-10 mb-6">Loading</div>
  </main>
</template>

<script>
  import DataTitle from '@/components/DataTitle';
  import { BASE_URL } from '../config';

  export default {
    name: 'Home',
    components: { DataTitle },
    data() {
      return {
        loading: true,
        title: 'Global',
        dataDate: '',
        status: {},
        countries: [],
      };
    },
    methods: {
      async fetchCovidData() {
        const res = await fetch(`${BASE_URL}/summary`);
        const data = await res.json();
        if (Object.keys(data).length > 0) {
          return data;
        }
      },
    },
    async created() {
      const data = await this.fetchCovidData();
      this.dataDate = data.Date;
      this.status = data.Global;
      this.countries = data.countries;
      this.loading = false;
    },
  };
</script>

<style scoped></style>
