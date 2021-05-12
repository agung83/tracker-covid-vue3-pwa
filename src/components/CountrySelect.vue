<template>
  <select
    @change="onChange"
    v-model="selected"
    class="form-select mb-2 block w-full border p-3 rounded"
  >
    <option value="0">Pilih Negara</option>
    <option
      v-for="(negara, index) in countries"
      :key="index"
      :value="negara.ID"
    >
      {{ negara.Country }}
    </option>
  </select>
</template>

<script>
export default {
  name: "CountrySelect",
  props: ["countries"],
  data() {
    return {
      selected: 0,
    };
  },
  methods: {
    onChange() {
      const negara = this.countries.find((item) => item.ID === this.selected);

      this.$emit("get-negara", negara); // parametes kedua ini adalah event dari anak ke parent nya
    },
  },
};
</script>