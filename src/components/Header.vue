<template>
  <header class="text-center bg-yellow-500 text-white p-4 mb-10">
    <div class="text-3xl md:text-5xl font-bold"><i class="fa fa-viruses"></i> Covid - 19 Tracker</div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  components: {},
  data () {
    return {
      loading: true
    }
  },
  methods: {
    async fetchCovidData () {
      const res = await fetch('https://api.covid19api.com/summary')
      const data = await res.json()
      return data
    }
  },
  async created () {
    const data = await this.fetchCovidData()
    console.log(data)
  }
}
</script>
