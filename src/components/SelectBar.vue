<template>
  <div>
    <form action="">
      <label for="s">Seleziona il genere
        <select  v-model="selected" for="s">Seleziona il genere
          <option name="Rock" id="Rock">Rock</option>
          <option name="Pop" id="Pop">Pop</option>
          <option name="Jazz" id="Jazz">Jazz</option>
          <option name="Metal" id="Metal">Metal</option>
        </select>
      </label>
    </form>
  </div>
</template>

<script>
export default {
  name: 'SelectBar',
  data() {
    return {
      selected: '',
    };
  },
};
</script>

<style lang="scss" scoped>
label{
  color: white;
  padding: 1rem;
}

</style>
