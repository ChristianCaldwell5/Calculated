<template>
  <router-view/>
</template>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.view-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  max-width: 1000px;
  margin: 0 auto;
}

.button--main {
    width: 100%;
    max-width: 500px;
    border: 4px solid #3eaf7c;
    color: #3eaf7c;
    padding: 10px;
    text-decoration: none;
    font-weight: bold;
    border-radius: 5px;
}
.mb--15 {
  margin-bottom: 15px;
}
</style>
