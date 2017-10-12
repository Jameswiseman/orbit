<template>
<div id="app">
  <div class="wrapper">
    <div class="header">
      <div class="logo">
        <router-link to="/" exact>
          <div v-html="logoIcon">

          </div>
        </router-link>
      </div>
      <div class="menu">
        <ul>
          <li>
            <router-link to="/" exact>Home</router-link>
          </li>
          <li>
            <router-link to="about" exact>About</router-link>
          </li>
        </ul>
      </div>
    </div>
  </div>
  <transition>
    <div class="page">
      <router-view/>
    </div>
  </transition>
</div>
</template>

<script>
import logoIcon from './assets/logo.svg'
export default {
  name: 'app',
  data: function () {
    return {
      logoIcon
    }
  }
}
</script>

<style lang="scss">
#app {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
.header {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    z-index: 9999;
    display: flex;
    flex: 1;
    justify-content: space-between;
}
.wrapper {
    position: relative;
    max-width: 1200px;
    width: 90vw;
    margin: auto;
}
.logo svg {
  width:50px;
}
.menu {
    ul {
        list-style: none;
        text-align: right;
        li {
            display: inline-block;
            a {
                color: white;
                text-decoration: none;
                text-transform: uppercase;
                padding: 10px 5px;
                &.active {
                    opacity: 0.5;
                }
            }
        }
    }
}
</style>
