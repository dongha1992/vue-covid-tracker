<template>
  <div class="grid md:grid-cols-2 gap-4">
    <div class="shadow-md bg-blue-100 p-10 text-center rounded">
      <h3 class="text-3l text-blue-900 font-bold mb-4">Cases</h3>
      <div class="text-2xl mb-4">
        <span class="font-bold">New:</span>
        {{ status.NewConfirmed }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">Total:</span>
        {{ status.TotalConfirmed }}
      </div>
    </div>
    <div class="shadow-md bg-blue-100 p-10 text-center rounded">
      <h3 class="text-3l text-blue-900 font-bold mb-4">Death</h3>
      <div class="text-2xl mb-4">
        <span class="font-bold">New:</span>
        {{ numberWithCommas(status.NewDeaths) }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">Total:</span>
        {{ numberWithCommas(status.TotalDeaths) }}
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'DataBoxes',
    props: ['status'],
    methods: {
      numberWithCommas(x) {
        return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
      },
    },
  };
</script>

<style scoped></style>
