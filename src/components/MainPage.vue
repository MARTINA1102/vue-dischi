<template>
  <div class="main">
    <div class="container">
      <ul v-if='arrCharacters'>
        <CardCharacter
          v-for = "character in arrCharacters"
          :key="character.title"
          :imgUrl="character.poster"
          :title="character.title"
          :author="character.author"
          :year="character.year"
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
  data() {
    return {
      arrCharacters: null,
      urlApi: 'https://flynn.boolean.careers/exercises/api/array/music',
    };
  },
  created() {
    axios.get(this.urlApi)
      .then((axiosResponse) => {
        console.log(axiosResponse.data);
        this.arrCharacters = axiosResponse.data.response;
      });
  },
  components: {
    CardCharacter,
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
