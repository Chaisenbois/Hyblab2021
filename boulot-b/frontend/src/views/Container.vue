<template>
  <div>
      <div id="wrapper">
      <img @click="backHome" id="wazzo" src="@/assets/wazzo.svg"/>
      <div id="buildings">
        <slot name="buildings"></slot>
      </div>
      <div id="question">
        <slot name="canari" ></slot>
        <slot name="question" ></slot>
      </div>

      <div id="stepper">
        <slot name="stepper" ></slot>
      </div>
      <slot/>
    </div>
  </div>
</template>

<script>
export default {
  name: "Container",
  methods: {
    backHome() {
      this.$root.$data.setActif(0)
    }
  }
}
</script>

<style scoped>
  #wrapper {
    position:relative;
    min-height: 100vh;
    top:0;
    bottom:0;
    left:0;
    right:0;
    display: grid;
    grid-template-columns: 0.9fr 1.2fr 0.9fr;
    grid-template-rows: 0.7fr 2fr 0.3fr;
    gap: 0 0;
    grid-template-areas:
      ". question ."
      ". question ."
      "stepper stepper stepper";
    overflow: hidden;

  }

#wazzo {
  cursor: pointer;
  position: relative;
  margin-left: 100px;
  margin-top: 40px;
  width: 40%;
  z-index: 12;
}




  #question {
    align-self: center;
    grid-area: question;
  }

  #stepper { grid-area: stepper; }

  #buildings {
    position: absolute;
    width: 100%;
    bottom: 0%;
  }

</style>