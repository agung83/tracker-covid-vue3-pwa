<template>
  <div class="grid md:grid-cols-2 gap-4">
    <!-- iko box 1 nyo yooy -->
    <div class="shadow-md bg-blue-100 p-10 text-center rounded">
      <h3 class="text-3xl text-blue-900 font-bold mb-4">Cases</h3>

      <div class="text-2xl mb-4">
        <span class="font-bold">New:</span>
        {{ NumberDenganKoma(stats.NewConfirmed) }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">Total:</span>
        {{ NumberDenganKoma(stats.TotalConfirmed) }}
      </div>
    </div>
    <!-- ko akhir box 1 -->
    <!-- iko box 2 nyo yooy -->
    <div class="shadow-md bg-blue-100 p-10 text-center rounded">
      <h3 class="text-3xl text-blue-900 font-bold mb-4">Deaths</h3>

      <div class="text-2xl mb-4">
        <span class="font-bold">New:</span>
        {{ NumberDenganKoma(stats.NewDeaths) }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">Total:</span>
        {{ NumberDenganKoma(stats.TotalDeaths) }}
      </div>
    </div>
    <!-- ko akhir box 2 -->
  </div>
</template>
<script>
export default {
  name: "DataBoxes",
  props: ["stats"],

  methods: {
    NumberDenganKoma(x) {
      return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
  },
};
</script>