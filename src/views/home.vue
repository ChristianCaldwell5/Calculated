<template>
    <div class="view-container">
        <h1>CALCULATED</h1>
        <hr>
        <h3>Select Mode</h3>
        <router-link class="button--main mb--15" to="/game">Addition/Subtraction</router-link>
        <router-link class="button--main mb--15" to="/game">Multiplication/Division</router-link>
        <router-link class="button--main mb--15" to="/game">Linear Equations</router-link>
        <router-link class="button--main mb--15" to="/game">Derivatives/Integrals</router-link>
    </div>
</template>

<script>
export default {
  name: 'Home',
}
</script>

<style scoped>

</style>
