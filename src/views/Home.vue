<template>
  <main v-if="!state.loading">
    <DataTitle :text="state.title" :dataDate="state.dataDate" />

    <CountrySelect @get-negara="GetDataNegara" :countries="state.countries" />
    <button
      @click="ResetData"
      v-if="state.status.Country"
      class="bg-green-700 text-white p-3 mt-2 mb-5 focus:outline-none hover:bg-green-600 rounded-xl"
    >
      Reset Data
    </button>

    <DataBoxes :stats="state.status" />
  </main>
  <main class="flex flex-col align-center justify-center text-center" v-else>
    <div class="text-gray-500 text-3xl mt-10">Fetching Data</div>
    <!-- <img :src="state.loadingImage" alt="" class="w-24 m-auto" /> -->
    <div class="flex justify-center ...">
      <div class="grid grid-cols-3">
        <div></div>
        <lottie-player
          :src="state.loadingImage"
          background="transparent"
          speed="1"
          loop
          autoplay
        ></lottie-player>
      </div>
    </div>
  </main>
</template>

<script>
import DataTitle from "@/components/DataTitle";
import DataBoxes from "@/components/DataBoxes";
import CountrySelect from "@/components/CountrySelect";
import { onMounted, reactive } from "vue";
export default {
  components: {
    DataTitle,
    DataBoxes,
    CountrySelect,
  },

  setup() {
    const state = reactive({
      loading: true,
      title: "",
      dataDate: "",
      status: {},
      countries: [],
      loadingImage: "/files/covid19.json",
    });

    const GetAsyncData = async () => {
      let res = await fetch("https://api.covid19api.com/summary");
      let data = await res.json();

      state.title = "GLOBAL";
      state.dataDate = data.Date;
      state.status = data.Global;
      state.countries = data.Countries;
      state.loading = false;
    };

    const GetDataNegara = (negara) => {
      state.status = negara;
      state.title = negara.Country;
    };

    const ResetData = () => {
      state.loading = true;
      GetAsyncData();
    };

    onMounted(() => {
      GetAsyncData();
    });

    return {
      ResetData,
      GetDataNegara,
      state,
    };
  },
};
</script>


