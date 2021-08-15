<script>
import Lazy from "./components/Lazy.vue";

export default {
  name: "App",
  components: {
    Lazy,
  },

  setup() {
    const thousandUsers = Array(1000)
      .fill({})
      .map((_, index) => ({
        id: index,
        name: `User ${index}`,
      }));

    return { thousandUsers };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.user {
  background: grey;
  min-height: 300px;
  margin-top: 100px;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>

<template>
  <Lazy
    v-for="user in thousandUsers"
    :key="user.index"
    :min-height="300"
    :unrender="true"
  >
    <div class="user">{{ user.name }}</div>
  </Lazy>
</template>
