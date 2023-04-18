<template>
  <div class="mt-10 grid md:grid-cols-2 mx-40 gap-10 flex justify-center font-bold">
    <div class="border-2 border-black mb-4 pb-4">
      <div class="text-center text-xl m-3">TOTAL</div>
      <div class="mx-3 text-orange-400">Confirmed:</div>
      <div class="mx-3 text-red-500">Death:</div>
      <div class="mx-3 text-green-700">Recovered:</div>
    </div>
    <div class="border-2 border-black mb-4 pb-4">
      <div class="text-center text-xl m-3 ">NEW</div>
      <div class="mx-3 text-orange-400">Confirmed:</div>
      <div class="mx-3 text-red-500">Death:</div>
      <div class="mx-3 text-green-700">Recovered:</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DataBoxes",
  props: ["stats"],
};
</script>
