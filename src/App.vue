<template>
  <div class="container">
    <div class="block" :class="{ animate: animateBlock }"></div>
    <button @click="handleAnimateBlock">Animate</button>
  </div>

  <div class="container">
    <transition name="para">
      <p v-if="paraIsVisible">
        This is the para which visible sometimes for this we need to test the
        animations
      </p>
    </transition>
    <button @click="togglePara">Toggle Para</button>
  </div>

  <base-modal @close="hideDialog" :open="dialogIsVisible">
    <p>This is a test dialog!</p>
    <button @click="hideDialog">Close it!</button>
  </base-modal>

  <div class="container">
    <button @click="showDialog">Show Dialog</button>
  </div>
</template>  

<script>
export default {
  data() {
    return {
      dialogIsVisible: false,
      animateBlock: false,
      paraIsVisible: false,
    };
  },
  methods: {
    showDialog() {
      this.dialogIsVisible = true;
    },
    hideDialog() {
      this.dialogIsVisible = false;
    },
    handleAnimateBlock() {
      this.animateBlock = !this.animateBlock;
    },
    togglePara() {
      this.paraIsVisible = !this.paraIsVisible;
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
html {
  font-family: sans-serif;
}
body {
  margin: 0;
}
button {
  font: inherit;
  padding: 0.5rem 2rem;
  border: 1px solid #810032;
  border-radius: 30px;
  background-color: #810032;
  color: white;
  cursor: pointer;
}
button:hover,
button:active {
  background-color: #a80b48;
  border-color: #a80b48;
}
.block {
  width: 8rem;
  height: 8rem;
  background-color: #290033;
  margin-bottom: 2rem;
  /* transition: transform 0.3s ease-out; */
}
.container {
  max-width: 40rem;
  margin: 2rem auto;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  padding: 2rem;
  border: 2px solid #ccc;
  border-radius: 12px;
}

.animate {
  /* transform: translateX(-150px); */
  /* it tells the element to be animated for the 0.3s and forward used for to tell the browser to accept the new state  */
  animation: box-slide 0.3s ease-out forwards;
}

.para-enter-from {
  /* opacity: 0;
  transform: translateY(-50px); */
}

.para-enter-active {
  animation: box-slide 0.3s ease-out;
}

.para-enter-to {
  /* opacity: 1;
  transform: translateY(0); */
}

.para-leave-from {
  /* opacity: 1;
  transform: translateY(0); */
}
.para-leave-active {
  animation: box-slide 0.3s ease-out;
}
.para-leave-to {
  /* opacity: 0;
  transform: translateY(-50px); */
}

@keyframes box-slide {
  0% {
    transform: translateY(-50px) scale(1);
  }
  75% {
    transform: translateY(-30px) scale(1.1);
  }
  100% {
    transform: translateY(0) scale(1);
  }
}
</style>