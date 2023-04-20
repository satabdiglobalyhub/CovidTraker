<template>
  <div class="h-2/4">
    <canvas ref="myChart"></canvas>
  </div>
</template>

<script>
import Chart from "chart.js/auto";

export default {
  mounted() {
    const ctx = this.$refs.myChart.getContext("2d");
    const myChart = new Chart(ctx, {
      type: "pie",
      data: {
        datasets: [
          {
            data: [12, 99, 3],
            borderWidth: 1,
            backgroundColor: [
              "rgb(251, 146, 62)",
              "rgb(239, 68, 68)",
              "rgb(23, 128, 61)",
            ],
          },
        ],
      },
      options: {
        legend: {
          display: false,
        },
        tooltips: {
          enabled: false,
        },
      },
    });
  },
};
</script>
