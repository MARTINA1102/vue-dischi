<template>
   <div class="header_nav">
    <img src="https://grafica-facile.com/wp-content/uploads/2022/01/spotify-logo.png" alt="logo">
    <SelectBar/>
  </div>
</template>

<script>
import SelectBar from './SelectBar.vue';

export default {
  name: 'HeaderPage',
  components: {
    SelectBar,
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
