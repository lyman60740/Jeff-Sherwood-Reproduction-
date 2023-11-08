<template>
  <nav>
    <div class="logo">
      <img src="logo.png" alt="Logo" />
    </div>
    <ul class="nav-links">
      <li><a href="#">Home</a></li>
      <li><a href="#">About</a></li>
      <li><a href="#">Services</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
  </nav>
</template>

<script setup></script>

<style scoped lang="scss">
nav {
  width: 100%;
  display: flex;
  justify-content: space-between;
  padding: 20px 0;
}
.nav-links {
  display: flex;
  & li:not(:last-child) {
    margin-right: 20px;
  }
}
</style>
