<template>
  <div class="h-1/4 w-2/4 p-4">
    <canvas ref="pieChart"></canvas>
  </div>
</template>

<script>
import Chart from "chart.js/auto";

export default {
  props: ["data"],
  data() {
    return {
      confirmed: "",
      death: "",
    };
  },

  computed: {
    chartData() {
      return [this.confirmed, this.death];
    },
  },

  methods: {
    destroyChart() {
      const chart = this.$refs.pieChart.chart;
      if (chart) {
        chart.destroy();
      }
    },

    async updated() {
      this.confirmed = await this.data.TotalConfirmed;
      this.death = await this.data.TotalDeaths;

      this.destroyChart();

      const ctx = this.$refs.pieChart.getContext("2d");
      const pieChart = new Chart(ctx, {
        type: "pie",
        data: {
          datasets: [
            {
              data: this.chartData,
              borderWidth: 0,
              backgroundColor: ["rgb(251, 146, 62)", "rgb(239, 68, 68)"],
            },
          ],
        },
        options: {
          animation: false,
          legend: {
            display: false,
          },
          tooltips: {
            enabled: true,
          },
        },
      });

      this.$refs.pieChart.chart = pieChart;
    },
  },

  watch: {
    data: {
      handler(newVal, oldVal) {
        if (newVal !== oldVal) {
          this.updated();
        }
      },
      deep: true,
    },
  },

  mounted() {
    this.updated();
  },
};
</script>
