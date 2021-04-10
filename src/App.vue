<template>
  <div id="app">
    <router-view />
  </div>
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Raleway:wght@300&display=swap");

$primary: #9b59b6;

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  width: 440px;
  margin: auto;
  margin-top: 8rem;
  font-family: "Raleway", sans-serif;
}
</style>
