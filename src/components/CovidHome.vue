<template>
  <body class="font-mono">
    <section class="text-center bg-cyan-300 text-black p-5 md:p-10">
      <div class="text-2xl md:text-6xl cursor-pointer flex justify-center">
        <img class="h-6 md:h-14" src="../assets/corona.png" /> COVID-19 STATS
      </div>
      <div class="text-xl md:text-2xl mt-4 cursor-pointer">
        API by:
        <a
          class="text-blue-800 underline"
          href="https://covid19api.com/"
          target="_blank"
          >Covid19api.com</a
        >
      </div>
    </section>

    <section class="bg-[#ffebcd] h-screen">
      <div class="text-xl flex justify-center p-2 md:p-5">
        Please select a Country
      </div>
      <div></div>
    </section>
  </body>
</template>

<script>
export default {
  name: "CovidHome",
  components: {},
  data() {
    return {
      loading: true,
      title: "Global",
      dataDate: "",
      stats: {},
      countries: [],
    };
  },
  methods: {
    async fetchCovidData() {
      const res = await fetch("https://api.covid19api.com/summary");
      const data = await res.json();
      return data;
    },
  },
  async created() {
    const data = await this.fetchCovidData();
    console.log(data);
  },
};
</script>
