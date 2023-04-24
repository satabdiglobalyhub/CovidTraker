<template>
  <div
    v-if="data != 0"
    class="grid lg:grid-cols-2 mx-40 gap-x-10 flex justify-center font-bold md:text-2xl cursor-pointer"
  >
    <div class="border-2 border-black mb-4 pb-4">
      <div>
        <div class="text-center m-3">TOTAL</div>
        <div class="mx-3 text-orange-400 flex justify-center">
          Confirmed:{{ data.TotalConfirmed.toLocaleString("en-IN") }}
        </div>
        <div class="mx-3 text-red-500 flex justify-center">
          Death:{{ data.TotalDeaths.toLocaleString("en-IN") }}
        </div>
        <!-- <div class="mx-3 text-green-700 flex justify-center">
          Recovered:{{ data.TotalRecovered.toLocaleString("en-IN") }}
        </div> -->
      </div>
      <div class="flex justify-center align-middle">
        <DataChart :confirmedCases="totalConfirmed" :deathCases="totalDeaths" />
      </div>
    </div>

    <div class="border-2 border-black mb-4 pb-4">
      <div>
        <div class="text-center m-3">NEW</div>
        <div class="mx-3 text-orange-400 flex justify-center">
          Confirmed:{{ data.NewConfirmed.toLocaleString("en-IN") }}
        </div>
        <div class="mx-3 text-red-500 flex justify-center">
          Death:{{ data.NewDeaths.toLocaleString("en-IN") }}
        </div>
        <!-- <div class="mx-3 text-green-700 flex justify-center">
          Recovered:{{ data.NewRecovered.toLocaleString("en-IN") }}
        </div> -->
      </div>
      <div class="flex justify-center align-middle">
        <DataChart :confirmedCases="newConfirmed" :deathCases="newDeaths" />
      </div>
    </div>
  </div>
</template>

<script>
import DataChart from "./DataChart.vue";

export default {
  name: "DataBoxes",
  props: ["data"],
  components: {
    DataChart,
  },
  data() {
    return {
      showDiv: false,
      totalConfirmed: "",
      totalDeaths: "",
    };
  },
  watch: {
    data: {
      handler(newVal, oldVal) {
        if (newVal != oldVal) {
          this.totalConfirmed = newVal.TotalConfirmed;
          this.totalDeaths = newVal.TotalDeaths;
          this.newConfirmed = newVal.NewConfirmed;
          this.newDeaths = newVal.NewDeaths;
        }
      },
      deep: true,
    },
  },
};
</script>
