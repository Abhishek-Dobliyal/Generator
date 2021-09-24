<template>
  <div class="container">
    <Header heading="Generator" subHeading="Generate Random Stuffs" color="#b08e12" borderColor="primary"></Header>
    <HomeBody></HomeBody>
  </div>
</template>

<script>
import Header from '../components/Header.vue'
import HomeBody from '../components/HomeBody.vue'

export default {
  name: "Home",
  components: {
    Header,
    HomeBody
  }
};
</script>
