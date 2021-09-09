<template>
  <div id="app">
    <Header :genres="genres" @genreSelector="selectedFilter"/>
    <main>
      <DiscVisualizer :filteredDiscs="filteredDiscs"/>
    </main>
  </div>
</template>

<script>
import Header from '@/components/Header.vue';
import DiscVisualizer from '@/components/DiscVisualizer.vue';

import axios from 'axios'

export default {
  name: 'App',
  components: {
    Header,
    DiscVisualizer
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
    filteredDiscs(){
      let sortedDiscs = [... this.discs]
      sortedDiscs.sort((a,b)=>a.year - b.year);
      if (this.genreFilter === 'All') return sortedDiscs;
      return sortedDiscs.filter(disc => disc.genre === this.genreFilter)
    }
  },
  created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music').then(res =>{
      this.discs = res.data.response
    })
  }
}
</script>

<style lang="scss">
@import 'scss/style.scss';
</style>
