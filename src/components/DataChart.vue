<template>
  <div class="h-1/4 w-2/4 p-4">
    <canvas ref="pieChart"></canvas>
  </div>
</template>

<script>
import Chart from "chart.js/auto";

export default {
  props: ["data", "confirmedCases", "deathCases"],
  data() {
    return {
      confirmed: "",
      death: "",
    };
  },

  computed: {
    chartData() {
      return [this.confirmedCases, this.deathCases];
    },
  },

  methods: {
    destroyChart() {
      const chart = this.$refs.pieChart.chart;
      if (chart) {
        chart.destroy();
      }
    },

    async updatedChart() {
      this.confirmed = await this.confirmedCases;
      this.death = await this.deathCases;

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
    confirmedCases: {
      handler(newVal, oldVal) {
        if (newVal !== oldVal) {
          this.updatedChart();
        }
      },
      deep: true,
    },
  },

  mounted() {
    this.updatedChart();
  },
};
</script>
