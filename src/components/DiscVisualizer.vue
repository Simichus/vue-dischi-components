<template>
  <div class="container">
      <div class="d-flex justify-content-center align-content-center flex-wrap pt-5">
          <div v-for="disc in filteredDiscs" :key="disc.title" class=" flex-shrink-0 w-20 p-4">
              <DiscCard :disc="disc"/>
          </div>
      </div>
  </div>
</template>

<script>
import DiscCard from '@/components/DiscCard.vue'
export default {
name:'DiscVisualizer',
components:{
    DiscCard
},
props:['filteredDiscs']
}
</script>

<style lang="scss" scoped>
.w-20{
    max-width: 20%;
}
</style>