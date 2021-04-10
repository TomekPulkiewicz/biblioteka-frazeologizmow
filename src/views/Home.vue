<template>
  <div class="home">
    <h1 v-if="selected != null" class="title">
      Wybrana Kategoria:
      <span style="color:#9b59b6">{{ selected.name }}</span>
    </h1>
    <h1 v-else class="title">Biblioteka Frazeologizmów</h1>
    <div class="categories">
      <button
        v-for="category in categories"
        :key="category.name"
        @click="selected = category"
      >
        {{ category.name }}
      </button>
    </div>
    <div class="search-box">
      <input type="text" placeholder="Szukaj" v-model="searchInput" />
    </div>
    <div class="phraseology" v-if="selected != null">
      <div class="card" v-for="data in searchedPhraseology" :key="data.name">
        <h3>{{ data.name }}</h3>
        <p>{{ data.data }}</p>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import categories from "../data.json";
export default {
  name: "Home",
  data() {
    return {
      categories: categories["categories"],
      selected: null,
      searchInput: "",
    };
  },
  computed: {
    searchedPhraseology: function() {
      return this.selected.data.filter((x) => {
        return (
          x.name.toUpperCase().match(this.searchInput.toUpperCase()) ||
          x.data.toUpperCase().match(this.searchInput.toUpperCase())
        );
      });
    },
  },
};
</script>

<style lang="scss">
.title {
  margin-bottom: 1.5rem;
}
.categories {
  display: flex;
  gap: 20px;
  margin-bottom: 1.5rem;
  button {
    padding: 7px;
    border: none;
    background-color: transparent;
    border: 1.5px solid #9b59b6;
    border-radius: 5px;
    color: #9b59b6;
  }
}
.phraseology {
  display: flex;
  flex-direction: column;

  .card {
    padding: 10px 2px;
    width: 440px;
    h3 {
      margin-bottom: 3px;
      letter-spacing: 0.2px;
    }
  }
}
.search-box {
  padding-bottom: 1rem;
  input {
    padding: 5px;
    width: 440px;
    border: 1.8px solid rgb(41, 41, 41);
    border-radius: 5px;
    height: 33px;
    font-size: 18px;
  }
}
</style>
