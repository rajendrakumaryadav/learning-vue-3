<template>
 <footer class="text-center bg-yellow-500 text-white p-4 mb-10">
    <p class="text-xs md:text-lg">Visit the source code <i class="fa fa-hand-point-right"/> <a class="text-blue-700" :href="gitRepoURL"><b>{{ gitRepoURL }}</b></a></p>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
  data () {
    return {
      gitRepoURL: 'https://github.com/rajendrakumaryadav/learning-vue-3'
    }
  }
}
</script>

<style scoped>

</style>
