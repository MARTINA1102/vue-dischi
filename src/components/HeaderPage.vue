<template>
   <div class="header_nav">
    <img src="https://grafica-facile.com/wp-content/uploads/2022/01/spotify-logo.png" alt="logo">
    <label for="select-genres">
      <select id="select-genres"
        v-model="genreFilter"
        name="genre"
        @change="genreChange">
        <option value="All"> All Genres</option>
        <option v-for="genre in genresList"
          :key="genre"
          :value="genre">
          {{genre}}
        </option>
      </select>
    </label>
  </div>
</template>

<script>
export default {
  name: 'HeaderPage',
  props: {
    genresList: Array,
  },
  data() {
    return {
      genreFilter: 'All',
    };
  },
  methods: {
    genreChange() {
      this.$emit('changedGenre', this.genreFilter);
    },
  },
};
</script>

<style lang="scss" scoped>
  img{
    height: 3rem;
    padding: 1rem;
  }
  .header_nav{
    background-color: rgb(39, 59, 79);
    height: 5rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
</style>
