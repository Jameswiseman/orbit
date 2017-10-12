<template>
  <section class="hero">
    <div class="strapline">
      <h1>Out of this world digital agency.</h1>
    </div>
    <div class="spaceman">
      <img src="../assets/spaceman.png" width="120px" />
    </div>
  </section>
</template>
<style lang="scss">
.logo-art {
  fill:white;
}
  .hero {
    background:black;
    position:absolute;
    top:0;
    left:0;
    right:0;
    bottom:0;
    display:flex;
    align-items: center;
    justify-content: center;
    &:after {
      content:'';
      position:absolute;
      top:0;
      left:0;
      right:0;
      bottom:0;
      background-image:url('../assets/earth.png');
      background-size:cover;
      background-position:center -1vh;
      background-repeat: no-repeat;
      animation: rise-bottom 50s ease-out both;
      will-change: transform;

    }
  }
  .strapline {
    text-align:center;
    position:relative;
    z-index:99;
    h1 {
      color:white;
      font-size:3em;
      letter-spacing: 2px;
      font-weight:lighter;
    }
  }
  .spaceman {
    position:absolute;
    top:25vh;
    left:-10vw;
    animation: spaceman-slide 200s cubic-bezier(0.250, 0.460, 0.450, 0.940) both;
    will-change: transform;
  }




// Animations

 @keyframes rise-bottom {
   0% {
             transform: scale(1) translateY(0);
             transform-origin: 50% 84%;
   }
   100% {
             transform: scale(1.25) translateY(15px);
             transform-origin: bottom;
   }
 }

@keyframes spaceman-slide {
  0% {
            transform: translateX(0) rotate(0deg);
  }
  100% {
            transform: translateX(150vw)  rotate(-40deg);
  }
}


</style>
