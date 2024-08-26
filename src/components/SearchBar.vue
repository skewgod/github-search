<template>
  <div class="search-bar">
    <input
      v-model="username"
      @keyup.enter="triggerSearch"
      type="text"
      placeholder="Search GitHub"
      class="search-input"
    />
    <button @click="triggerSearch" class="search-button">Search</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: ''
    }
  },
  methods: {
    triggerSearch() {
      if (this.username) {
        this.$emit('search', this.username)
      }
    }
  }
}
</script>

<style scoped>
.search-bar {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  max-width: 100%;
  margin: 0 auto;
  padding: 16px;
}

.search-input {
  padding: 12px 16px;
  font-size: 16px;
  width: 100%;
  max-width: 400px;
  margin-right: 8px;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  outline: none;
  transition:
    border-color 0.3s,
    box-shadow 0.3s;
}

.search-input:focus {
  border-color: #007bff;
  box-shadow: 0 4px 6px rgba(0, 123, 255, 0.2);
}

.search-button {
  padding: 12px 24px;
  font-size: 16px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition:
    background-color 0.3s,
    box-shadow 0.3s;
}

.search-button:hover {
  background-color: #0056b3;
  box-shadow: 0 4px 6px rgba(0, 123, 255, 0.3);
}

@media (max-width: 600px) {
  .search-bar {
    flex-direction: column;
  }

  .search-input {
    margin-right: 0;
    margin-bottom: 8px;
    max-width: 600px;
  }

  .search-button {
    width: 100%;
  }
}
</style>
