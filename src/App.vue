<template>
  <div id="app">
    <div class="search-container">
      <SearchBar @search="handleSearch" :searchType="searchType" />
      <div class="toggle-container">
        <label>
          <input type="radio" value="users" v-model="searchType" />
          Search Users
        </label>
        <label>
          <input type="radio" value="repositories" v-model="searchType" />
          Search Repositories
        </label>
      </div>
    </div>

    <PageLoader v-if="loading" />

    <div v-if="items.length" class="list-container">
      <transition-group name="list" tag="div">
        <component :is="componentType" v-for="item in items" :key="item.id" :item="item" />
      </transition-group>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import SearchBar from './components/SearchBar.vue'
import RepoItem from './components/RepoItem.vue'
import UserItem from './components/UserItem.vue'
import PageLoader from './components/PageLoader.vue'

export default {
  name: 'App',
  components: {
    SearchBar,
    RepoItem,
    UserItem,
    PageLoader
  },
  data() {
    return {
      items: [],
      loading: false,
      searchType: 'users'
    }
  },
  computed: {
    componentType() {
      return this.searchType === 'repositories' ? 'RepoItem' : 'UserItem'
    }
  },
  watch: {
    searchType() {
      this.items = []
    }
  },
  methods: {
    async handleSearch(query) {
      this.loading = true
      const endpoint =
        this.searchType === 'users'
          ? `https://api.github.com/search/users?q=${query}`
          : `https://api.github.com/search/repositories?q=${query}`

      try {
        const response = await axios.get(endpoint)
        this.items = response.data.items
      } catch (error) {
        console.error('Error fetching data:', error)
        this.items = []
      } finally {
        this.loading = false
      }
    }
  }
}
</script>

<style>
#app {
  margin: 50px auto;
  font-family: Arial, sans-serif;
}

.search-container {
  max-width: 600px;
  text-align: center;
  margin: 0 auto;

  margin-bottom: 20px;
}

.toggle-container {
  margin-top: 10px;
}

.toggle-container label {
  margin-right: 20px;
  font-size: 16px;
  color: #24292e;
}

.list-container {
  max-height: calc(100vh - 240px);
  max-width: 50%;
  overflow-y: auto;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;

  margin: 0 auto;
}

.list-enter-from {
  opacity: 0;
  transform: scale(0.6);
}

.list-enter-to {
  opacity: 1;
  transform: scale(1);
}

.list-enter-active {
  transition: all 0.5s ease;
}

@media (max-width: 600px) {
  .list-container {
    max-width: 90%;
  }
}
</style>
