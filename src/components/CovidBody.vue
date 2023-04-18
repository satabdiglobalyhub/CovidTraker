<template>
  <div class="bg-[#ffebcd] h-full md:h-screen">
    <CountrySelector @Country="CountryName" @UpdatedDate="newDate" />
    <DataBoxes />
    <div class="flex justify-center align-middle m-10 text-xl md:text-3xl">
      Updated: {{ Date }}
    </div>
  </div>
</template>

<script>
import CountrySelector from "./CountrySelector.vue";
import DataBoxes from "./DataBoxes.vue";

export default {
  name: "CovidBody",
  components: {
    CountrySelector,
    DataBoxes,
  },
  data() {
    return {
      Date: "",
    };
  },
  methods: {
    newDate(data) {
      this.Date = data;
    },
  },
};
</script>
