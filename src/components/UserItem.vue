<template>
  <div class="user-item">
    <img :src="item.avatar_url" alt="Avatar" class="avatar" />
    <div class="info">
      <h3>{{ item.login }}</h3>
      <a :href="item.html_url" target="_blank" class="profile-link">View Profile</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'UserItem',
  props: {
    item: Object
  }
}
</script>

<style scoped>
.user-item {
  display: flex;
  align-items: center;
  padding: 15px;
  border-radius: 12px;
  background-color: #ffffff;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  transition:
    box-shadow 0.3s,
    transform 0.3s;
  margin-bottom: 12px;
  cursor: pointer;
}

.user-item:hover {
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.2);
  transform: translateY(-2px);
}

.avatar {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  margin-right: 15px;
  border: 2px solid #e1e4e8;
}

.info {
  flex: 1;
}

h3 {
  margin: 0 0 8px;
  font-size: 18px;
  color: #333333;
}

.profile-link {
  color: #1e88e5;
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s;
}

.profile-link:hover {
  color: #1565c0;
  text-decoration: underline;
}
</style>
