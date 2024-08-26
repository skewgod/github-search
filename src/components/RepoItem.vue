<template>
  <div class="repo-item">
    <h3>{{ item.name }}</h3>
    <p>{{ item.description }}</p>
    <a :href="item.html_url" target="_blank" class="github-link"> View on GitHub </a>
  </div>
</template>

<script>
export default {
  props: {
    item: Object
  }
}
</script>

<style scoped>
.repo-item {
  background: #ffffff;
  margin: 12px 0;
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  transition:
    box-shadow 0.3s,
    transform 0.3s;
  cursor: pointer;
}

.repo-item:hover {
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.2);
  transform: translateY(-2px);
}

h3 {
  margin: 0 0 12px;
  font-size: 20px;
  color: #333333;
}

p {
  margin: 0 0 15px;
  font-size: 14px;
  color: #606060;
}

.github-link {
  color: #1e88e5;
  text-decoration: none;
  font-weight: 500;
  display: inline-block;
  padding: 6px 12px;
  border: 2px solid transparent;
  border-radius: 6px;
  transition:
    background-color 0.3s,
    border-color 0.3s;
}

.github-link:hover {
  background-color: #e3f2fd;
  border-color: #1e88e5;
  text-decoration: none;
}
</style>
