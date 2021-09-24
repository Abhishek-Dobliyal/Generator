<template>
    <Header heading="Quote Generator" subHeading="Generates quotes of all kind" color="red" borderColor="danger"></Header>
    <div class="container mt-4 text-center">
        <div class="container mt-5 bg-dark text-light p-3" v-if="quote">
            <blockquote class="blockquote">
                <p>{{quote}}</p>
            </blockquote>
            <figcaption class="blockquote-footer">
                <cite>{{author}}</cite>
            </figcaption>
        </div>
        <button @click="getQuote" class="btn btn-outline-danger mt-3">Fetch Quote</button>
    </div>
</template>

<script>
import Header from '../components/Header.vue'
export default {
    name: 'Quote',
    components: {
        Header
    },
    data() {
        return {
            quote: '',
            author: ''
        }
    },
    methods: {
        getQuote() {
            const url = 'https://api.quotable.io/random';
            fetch(url).then((res) => {
                return res.json()
            }).then((data) => {
                this.quote = data.content;
                this.author = data.author;
            })
        }
    }

}
</script>

<style>

</style>