
<template>
<transition name="fade">
  <div id="app">
    <div class="wrapper">
      <div class="header">
        <div class="logo"  @mouseenter="startRotate" @mouseleave="stopRotate">
          <router-link to="/" exact>
            <div v-html="logoIcon">

            </div>
            <span>orbit</span>
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
</transition>
</template>

<script>
import logoIcon from './assets/logo-2.svg'
import {
  TweenMax
  // EasePack
} from 'gsap'
export default {
  name: 'app',
  data: function () {
    return {
      logoIcon,
      loaded: false,
      orbitAnimation: ''
    }
  },
  methods: {
    startRotate () {
      this.orbitAnimation.paused(false)
    },
    stopRotate () {
      this.orbitAnimation.pause()
    }
  },
  mounted: function () {
    this.orbitAnimation = new TweenMax('.planet', 10, {
      bezier: {
        values: [{
          x: 0,
          y: 0
        }, {
          x: -165,
          y: 70
        }, {
          x: 0,
          y: 140
        }, {
          x: 165,
          y: 70
        }, {
          x: 0,
          y: 0
        }]
      },
      // ease: EasePack.Linear.easeNone,
      force3D: true,
      paused: true,
      repeatDelay: 0,
      ease: Linear.easeNone,
      repeat: -1,
      yoyo: false
    })
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
    will-change: opacity;
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
.logo {
    font-size: 1.4em;
    color: white;

    svg {
        width: 2em;
        display: inline-block;
        vertical-align: -0.5em;
        .orbit {

            transform-origin: center center;
            transform: rotate(-45deg);
            .path {
                stroke: white;
                stroke-width: 5px;
            }
            .planet {
                fill: white;
            }
        }

    }
    a {
        color: white;
        text-decoration: none;
        letter-spacing: 0.1em;
    }
    div {
        display: inline-block;
    }
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
.fade-enter-active,
.fade-leave-active {
    transition: opacity 1s ease-in;
}

.fade-enter,
.fade-leave-to {
    opacity: 0;
}
</style>
