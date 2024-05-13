<template>
  <footer>
    <p>Copyright &copy; 2024</p>
    <router-link v-show="homePage" to="/about">About</router-link>
  </footer>
</template>

<script>
export default {
  name: "Footer",
  computed: {
    homePage() {
      return this.$route.path === "/"
    }
  }
}
</script>

<style scoped>
a {
  color: #333;
}

footer {
  margin-top: 30px;
  text-align: center;
}
</style>