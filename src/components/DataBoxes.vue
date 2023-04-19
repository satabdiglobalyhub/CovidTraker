<template>
  <div
    class="mt-10 grid md:grid-cols-2 mx-40 gap-10 flex justify-center font-bold md:text-2xl"
  >
    <div class="border-2 border-black mb-4 pb-4">
      <div class="text-center m-3">TOTAL</div>
      <div class="mx-3 text-orange-400 flex justify-center">
        Confirmed:{{ data.TotalConfirmed }}
      </div>
      <div class="mx-3 text-red-500 flex justify-center">
        Death:{{ data.TotalDeaths }}
      </div>
      <div class="mx-3 text-green-700 flex justify-center">
        Recovered:{{ data.TotalRecovered }}
      </div>
    </div>

    <div class="border-2 border-black mb-4 pb-4">
      <div class="text-center m-3">NEW</div>
      <div class="mx-3 text-orange-400 flex justify-center">
        Confirmed:{{ data.NewConfirmed }}
      </div>
      <div class="mx-3 text-red-500 flex justify-center">
        Death:{{ data.NewDeaths }}
      </div>
      <div class="mx-3 text-green-700 flex justify-center">
        Recovered:{{ data.NewRecovered }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DataBoxes",
  props: ["data"],
};
</script>
