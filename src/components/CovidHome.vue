<template>
  <body class="font-mono">
    <CovidHeader />
    <CovidBody />
  </body>
</template>

<script>
import CovidHeader from "./CovidHeader.vue";
import CovidBody from "./CovidBody.vue";

export default {
  components: {
    CovidHeader,
    CovidBody,
  },
};
</script>
