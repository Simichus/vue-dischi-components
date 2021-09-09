<template>
  <div id="app">
    <Header :genres="genres" @genreSelector="selectedFilter"/>
  </div>
</template>

<script>
import Header from '@/components/Header.vue';

import axios from 'axios'

export default {
  name: 'App',
  components: {
    Header
  },
  data(){
    return{
      discs: [],
      genreFilter:'All',
    }
  },
  methods:{
    selectedFilter(filter){
      this.genreFilter = filter
    }
  },
  computed:{
    genres() {
      const genres = [];
      this.discs.forEach((disc) => {
        if (!genres.includes(disc.genre)) genres.push(disc.genre);
      });
      return genres;
    },
  },
  created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music').then(res =>{
      this.discs = res.data.response
      console.log(this.discs)
    })
  }
}
</script>

<style lang="scss">
@import 'scss/style.scss';
</style>
