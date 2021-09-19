<template>
  <Header />
  <main class="justify-around ml-10 md:ml-8 mb-5 mr-5" v-if="!loading">
    <DataTitle :data-date="dataDate" :text="title"/>
    <DataBoxes :stats="stats"/>
    <CountrySelect @get-country="getCountryData" :countries="countries"/>
    <button
      v-if="stats.Country"
      @click="clearCountryData"
      class="w-full md:w-2/3 md:content-center bg-red-500 text-white rounded p-3 mt-10 focus:outline-none hover:bg-red-600"> <i class="fa fa-trash-alt"/> Clear Country </button>
  </main>
  <main v-else class="flex flex-col align-center justify-center text-center">
    <div class="text-gray-500 text-3xl mt-10 mb-6">
      Fetching Data
    </div>
    <img :src="loadingImage" alt="hour-glass Image" class="w-24 m-auto"/>
  </main>
</template>

<script>

import DataTitle from '@/components/DataTitle'
import DataBoxes from '@/components/DataBoxes'
import CountrySelect from '@/components/CountrySelect'

export default {
  name: 'Home',
  components: { CountrySelect, DataBoxes, DataTitle },
  data () {
    return {
      loading: true,
      title: 'Global',
      dataDate: '',
      stats: {},
      countries: {},
      loadingImage: require('../assets/loading.gif')
    }
  },
  methods: {
    async fetchCovidData () {
      const res = await fetch('https://api.covid19api.com/summary')
      const data = await res.json()
      return data
    },
    getCountryData (country) {
      this.stats = country
      this.title = country.Country
    },
    async clearCountryData () {
      this.loading = true
      const data = await this.fetchCovidData()
      this.title = 'Global'
      this.stats = data.Global
      this.loading = false
    }
  },
  async created () {
    const data = await this.fetchCovidData()
    console.log(data)
    this.dataDate = data.Date
    this.stats = data.Global
    this.countries = data.Countries
    this.loading = false
  }
}
</script>
