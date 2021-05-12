<template>
  <div class="text-center">
    <h2 class="text-3xl font-bold">{{ text }}</h2>
    <div class="text-2xl mt-4 mb-10">
      {{ dataDate }}

      <!-- //custom moment surang yoo -->
    </div>
  </div>
</template>


<script>
export default {
  name: "DataTitle",
  props: ["text", "dataDate"],
};
</script>