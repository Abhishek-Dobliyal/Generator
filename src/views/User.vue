<template>
  <Header heading="Fake User Generator" subHeading="Generates a user with fake name, email & phone" color="cyan" borderColor="info"></Header>
  <div class="container mt-5">
    <div class="container text-center bg-dark text-light border border-info rounded-3 border-3">
      <div class="col-md" v-for="user in details" :key="user">
        <div class="row py-2">
          <span>Name: <span class="lead">{{user.name.first + ' ' + user.name.last}}</span></span>
        </div>
        <div class="row py-2">
          <span>Email: <span class="lead">{{user.email}}</span></span>
        </div>
        <div class="row py-2">
          <span>Phone: <span class="lead">{{user.phone}}</span></span>
        </div>
        <div class="row py-2">
          <span>Gender: <span class="lead">{{user.gender}}</span></span>
        </div>
        <img :src="profilePic" class="mt-2 rounded border border-info border-4" alt="">
      </div>
      <button class="btn btn-outline-info my-4" @click="fetchDetails">Fetch User</button>
    </div>
  </div>
</template>

<script>
import Header from '../components/Header.vue'

export default {
  name: 'User',
  components: {
    Header
  },
  data() {
    return {
      details: undefined,
      profilePic: ''
    }
  },
  methods: {
    fetchDetails() {
      const url = 'https://randomuser.me/api';
      fetch(url).then((res) => {
        return res.json()
      }).then((data) => {
        this.details = data.results;
        this.profilePic = this.details[0].picture.large;
        console.log(this.profilePic)
      })
    }
  }
}
</script>

<style>

</style>
