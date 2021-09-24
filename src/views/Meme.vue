<template>
  <Header heading="Meme Generator" subHeading="Fetches popular memes directly from Reddit" color="seagreen" borderColor="success"></Header>
  <div class="container mt-3 text-center">
      <div class="container w-50 h-50 my-4">
        <img :src="memeUrl" v-if="memeUrl" class="img-fluid border rounded border-3 border-success" alt="Meme">
      </div>
      <button class="btn btn-outline-success my-4" @click="fetchMeme">Fetch Meme</button>
  </div>
</template>

<script>
import Header from '../components/Header.vue'
export default {
    name: "Meme",
    components: {
        Header
    },

    data() {
        return {
            memeUrl: ''
        }
    },
    methods: {
        getRandom(n) {
            return Math.floor(((Math.random() * n) + 1))
        },

        fetchMeme() {
            const count = this.getRandom(50);
            const apiUrl = 'https://meme-api.herokuapp.com/gimme/' + count; 
            fetch(apiUrl).then((res) => {
                return res.json()
            }).then((data) => {
                const memeNumber = this.getRandom(count)
                this.memeUrl = data.memes[memeNumber].url;
            })
        }
    }
}
</script>
