<template>
  <div class="disc-card p-4 text-center">
      <figure>
      <img :src="disc.poster" :alt="disc.title">
      </figure>
      <h2 class="fs-4">{{disc.title}}</h2>
      <h5>{{disc.author}}</h5>
      <h5>{{disc.year}}</h5>
  </div>
</template>

<script>
export default {
name:'DiscCard',
props:['disc']
}
</script>

<style lang="scss" scoped>
@import '../scss/_vars.scss';

.disc-card{
    background-color: $light-gray;
    min-height: 400px;
    figure{
        min-height: 180px;
        
        img{
            max-width: 100%;
        }
    }

    h5{
        font-size: 16px;
        color: gray;
    }
}
</style>