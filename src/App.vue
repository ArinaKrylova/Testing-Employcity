<template>
  <div id="app">
    <Header/>

    <main>
      <HomeView />
    </main>

    <Footer />
  </div>
</template>

<script setup>
import Footer from "./components/layout/Footer.vue";
import HomeView from "./components/views/HomeView.vue";
import Header from "./components/layout/Header.vue";
</script>