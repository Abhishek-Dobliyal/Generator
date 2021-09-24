<template>
  <div class="container text-center mt-2">
    <div :class="`p-3 text-left bg-dark text-light border border-${borderColor} rounded-3 border-3`">
        <h3 class="display-4 m-3">{{ heading }}</h3>
        <span class="lead" :style="`color: ${color}`">{{ subHeading }}</span>
    </div>
  </div>
</template>

<script>
export default {
    name: 'Header',
    props: {
        heading: String,
        subHeading: String,
        color: String,
        borderColor: String
    }
}
</script>

<style scoped>

</style>