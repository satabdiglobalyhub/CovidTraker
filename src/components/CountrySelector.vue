<template>
  <section>
    <div class="text-xl flex justify-center p-2 md:p-5">
      <img v-if="loading" src="../assets/loading.gif" alt="Loading..." />
      <div v-else class="md:text-4xl mt-4 md:p-4">
        <select
          @change="fetchCountry"
          class="bg-gray-400 border-2 rounded text-center w-11/12 flex justify-center p-1 m-2.5"
          v-model="selected"
        >
          <option value="0">Select a country</option>
          <option v-for="country in countries" :value="country.ID">
            {{ country.Country }}
          </option>
        </select>
        <div
          class="mt-10 flex justify-center text-4xl underline underline-offset-2 md:text-6xl cursor-pointer"
        >
          {{ title }}
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "CountrySelector",
  components: {},
  data() {
    return {
      loading: true,
      title: "Global",
      dataDate: "",
      stats: {},
      countries: [],
      selected: "0",
    };
  },
  methods: {
    async fetchCovidData() {
      const res = await fetch("https://api.covid19api.com/summary");
      const data = await res.json();
      return data;
    },
    fetchCountry(event) {
      const selectedCountryID = this.selected;
      if (selectedCountryID === "0") {
        this.title = "Global";

        this.$emit("country", this.stats);
      } else {
        const selectedCountry = this.countries.find(
          (country) => country.ID === selectedCountryID
        );
        // this.title = selectedCountry.Country;
        this.title = "";
        this.$emit("country", selectedCountry);
      }
    },
  },
  async created() {
    const data = await this.fetchCovidData();
    // console.log(data);

    const Updateddate = data.Date;
    this.$emit("updatedDate", Updateddate);
    this.stats = data.Global;
    this.$emit("country", this.stats);
    this.countries = data.Countries;
    this.loading = false;
  },
};
</script>
