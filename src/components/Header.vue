<template>
  <header class="text-center bg-yellow-500 text-white p-4 mb-10">
    <div class="text-2xl md:text-5xl font-bold"><i class="fa fa-viruses"></i> Global Covid - 19 Tracker <i class="fa fa-pump-medical"/></div>
    <p class="text-sm md:text-lg">Based on <a class="text-blue-700" :href="apiurl" target="_blank">Covid-19 API Data</a> and Tutorials by <b>{{ taughtBy }}</b></p>
  </header>
</template>

<script>
export default {
  name: 'Header',
  components: {},
  data () {
    return {
      apiurl: 'https://covid19api.com',
      taughtBy: 'Traversy Media'
    }
  }
}
</script>
