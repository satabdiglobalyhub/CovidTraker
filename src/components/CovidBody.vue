<template>
  <div class="bg-[#ffebcd] h-full md:h-full">
    <CountrySelector @updatedDate="newDate" @country="countryData" />
    <DataBoxes :data="Data" />

    <div class="flex flex-col items-center m-10 text-xl md:text-3xl gap-4">
      <div class="cursor-pointer">Updated:</div>
      <div class="cursor-pointer pb-10">
        {{ this.Date }}
      </div>
    </div>
  </div>
</template>

<script>
import CountrySelector from "./CountrySelector.vue";
import DataBoxes from "./DataBoxes.vue";

export default {

  components: {
    CountrySelector,
    DataBoxes,
  },
  data() {
    return {
      Date: "",
      Data: "",
    };
  },
  methods: {
    newDate(data) {
      const date = new Date(data);
      const updatedDate = date.toLocaleDateString("en-CA", {
        year: "numeric",
        month: "2-digit",
        day: "2-digit",
        hour: "2-digit",
      });
      this.Date = updatedDate;
    },
    countryData(data) {
      this.Data = data;
    },
  },
};
</script>
