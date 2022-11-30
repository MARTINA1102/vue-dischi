<template>
  <div class="main">
    <div class="container">
      <ul v-if='arrCharacters'>
        <CardCharacter
          v-for = "character in arrDiscFiltered"
          :key="character.title"
          :imgUrl="character.poster"
          :title="character.title"
          :author="character.author"
          :year="character.year"
          :genere="character.genre"
        />
      </ul>
      <div v-else>..LOADING..</div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import CardCharacter from './CardCharacter.vue';

export default {
  name: 'MainPage',
  components: {
    CardCharacter,
  },
  data() {
    return {
      arrCharacters: null,
      urlApi: 'https://flynn.boolean.careers/exercises/api/array/music',
    };
  },
  props: {
    genreFilter: String,
  },
  computed: {
    arrGenres() {
      const arrGenres = [];
      if (this.arrCharacters) {
        this.arrCharacters.forEach((objDisc) => {
          if (!arrGenres.includes(objDisc.genre)) {
            arrGenres.push(objDisc.genre);
          }
        });
      }
      return arrGenres;
    },
    arrDiscFiltered() {
      if (this.genreFilter === 'All') {
        return this.arrCharacters;
      }
      return this.arrCharacters.filter((objDisc) => objDisc.genre === this.genreFilter);
    },
  },
  watch: {
    arrGenres(newValue) {
      this.$emit('genresReady', newValue);
    },
  },
  created() {
    axios.get(this.urlApi)
      .then((axiosResponse) => {
        console.log(axiosResponse.data);
        this.arrCharacters = axiosResponse.data.response;
      });
  },
};
</script>

<style lang="scss" scoped>
.main{
  background-color:rgb(16, 31, 48);
  padding-top: 4rem;
}
.container{
  max-width: 1200px;
  margin: 0 auto;
}
ul{
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}

</style>
