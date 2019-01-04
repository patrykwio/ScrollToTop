<template>
  <button v-bind:class="{ visible: isActive }">{{buttonText}}</button>
</template>

<script>
export default {
  name: "ScrollToTop",
  data() {
      return {
          buttonText: "Go to Top", //inner text of button element
          isActive: false, // status false for invisible on beginig
          scrollActivatePossition: 300, //possition of activate point from top in pixels
          scrollStep: 10, // step distance resolution for moving (speed contol variable)
          scrollTimeout: 1 // step time resolution in miliseconds (speed contol variable)
      }
  },
  mounted() {
    let btn = this.$el; //button handle
    btn.addEventListener("click", this.scrollToTop); //listener for button
    window.addEventListener("scroll", this.buttonState); //observer for window possition
  },
  methods: {
    scrollToTop: function() {
      let self = this; //keep instance (for setTimeout)
      if (window.scrollY != 0) { //if window not on top
        setTimeout(function() { // do job after setted time
          window.scrollTo(0, window.scrollY - self.scrollStep); //move window up by step
          self.scrollToTop(); //recursion (do yourself)
        }, self.scrollTimeout); // run after setted time
      }
    },
    buttonState() {
      this.isActive = (window.scrollY >= this.scrollActivatePossition) ? true : false;
    }
  }
};
</script>

<style lang="css" scoped>

  button {
    /* layer */
    z-index:9999;  
    /* possition */
    position:fixed;
    right:0;
    bottom:20%;
    /* state */
    opacity:0;
    /* look - font */
    font-size: 1.2rem;
    font-weight: bold;
    color: rgb(200,200,255);
    /* look - button */
    background:rgba(0,0,204,.6);
    border:none;
    padding:1rem;
    border-radius: 20px 0 0 20px;
    /* animate effect */
    transition: opacity .2s linear; 
  }
  button.visible {
    opacity:1;
  }
</style>