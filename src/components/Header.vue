<template>
  <header class="py-3">
      <div class="container d-flex justify-content-between align-items-center">
      <img src="https://upload.wikimedia.org/wikipedia/commons/7/71/Spotify.png" alt="">
      <select @change="$emit('genreSelector', selectedFilter)" v-model="selectedFilter" name="genre-select" id="genre-select">
          <option selected value="All">All</option>
          <option v-for="genre in genres" :key="genre" :value="genre">{{genre}}</option>
      </select>
      </div>
  </header>
</template>

<script>
export default {
    name: 'Header',
    props:['genres'],
    data(){
        return{
            selectedFilter:'All'
        }
    }

}
</script>

<style scoped lang="scss">
@import '../scss/_vars.scss';

    header{
        background-color: $light-gray;
        box-shadow: 0px 2px 2px rgba($color: #000, $alpha: 0.2);

        div{
            height: 75px;
        }

    }
    img{
        max-height: 100%;
    }

    select{
        height: 25px;
    }
</style>