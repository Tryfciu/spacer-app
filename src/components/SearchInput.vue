<template>
    <div class="searchWrapper">
        <input
        id="search"
        name="search"
        v-model="searchValue"
        @input="handleInput"
        />
      <ul>
        <li v-for="result in results" :key="result.data[0].nasa_id">
          <p>{{ result.data[0].description }}</p>
        </li>
      </ul>
    </div>
</template>

<script>
export default {
  name: 'SearchInput',
};
</script>

<style lang="scss" scoped>
.searchWrapper {
  margin-top: 50px;
  display: flex;
  flex-direction: column;
  width: 300px;

  input {
    height: 30px;
    border: 0;
    background: none;
    border-bottom: 1px solid black;
  }
}
</style>

