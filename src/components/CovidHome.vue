<template>
  <body class="font-mono">
    a
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
