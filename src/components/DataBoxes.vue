<template>
  <div class="grid md:grid-cols-2 gap-4">
    <!--    Cases-->
    <div class="shadow-md bg-yellow-100 p-10 text-center rounded">
      <h3 class="text-3xl text-yellow-500 font-bold mb-4"><i class="fa fa-pump-medical"></i> Cases</h3>
      <div class="text-xl mb-4">
        <span class="font-bold"> New : </span>
        {{ formattedNewConfirmed }}
      </div>
      <div class="text-xl mb-4">
        <span class="font-bold">Total : </span>
        {{ formattedTotalCase }}
      </div>
    </div>
    <!--  Deaths -->
    <div class="shadow-md bg-yellow-100 p-10 text-center rounded">
      <h3 class="text-3xl text-yellow-500 font-bold mb-4"><i class="fa fa-skull"></i> Deaths</h3>
      <div class="text-xl mb-4">
        <span class="font-bold"> New : </span>
        {{ formattedNewDeaths }}
      </div>
      <div class="text-xl mb-4">
        <span class="font-bold">Total : </span>
        {{ formattedTotalDeaths }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DataBoxes',
  props: ['stats'],
  methods: {
    getLocaleObject () {
      return new Intl.NumberFormat('en-IN')
    }
  },
  computed: {
    formattedNewConfirmed: function () {
      return this.getLocaleObject().format(this.stats.NewConfirmed)
    },
    formattedTotalCase: function () {
      return this.getLocaleObject().format(this.stats.TotalConfirmed)
    },
    formattedNewDeaths: function () {
      return this.getLocaleObject().format(this.stats.NewDeaths)
    },
    formattedTotalDeaths: function () {
      return this.getLocaleObject().format(this.stats.TotalDeaths)
    }
  }
}
</script>
