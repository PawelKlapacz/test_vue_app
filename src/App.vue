<template>
  <header>Reaction Timer</header>
  <div>
    <button class="button" :disabled="this.runningGame" @click="startGame">Play</button>
  </div>
  <div v-if="isPlaying">
    <Block @close="finishGame"> </Block>
  </div>
  <div v-if="showResult">
    <Results :message="this.sentMessage" @click="toggleResult"> </Results>
  </div>
</template>


<script>
import Block from './components/Block.vue';
import Results from './components/Results.vue'

export default {

  components: {
    Block, 
    Results
  },

  data() {
    return {
      runningGame: false,
      counter: 0,
      randomTime: 0,
      isPlaying: false,
      clickStart: 0,
      reactionTime: 0,
      showResult: false,
      sentMessage: "",
    }
  },

  methods: {
    toggleBlock() {
      this.isPlaying = !this.isPlaying
    },

    startGame() {
      this.randomTime = (2 + Math.random() * 5) * 1000;
      this.runningGame = !this.runningGame;
      this.showResult = false;
      setTimeout(() => {
        this.toggleBlock();
        this.clickStart = performance.now();
      }, this.randomTime);
    },

    finishGame(data) {
      this.toggleBlock();
      this.runningGame = !this.runningGame;
      this.reactionTime = ((data - this.clickStart)/1000).toFixed(4);
      this.sentMessage = 'Your result is: ' + this.reactionTime + ' seconds'
      this.toggleResult()
    },

    toggleResult() {
      this.showResult = !this.showResult
    }    
  }

}
</script>


<style scoped>
header {
  font-size: 5rem;
  color: green;
  font-family: Georgia;
  text-align: center;
}

.button {
  margin: 2rem auto;
  display: block;
  background-color: aqua;
  color: black;
  font-size: 3rem;
  place-items: center;
  border-radius: 10px;
}

.button:disabled {
  margin: 2rem auto;
  display: block;
  background-color: rgb(206, 209, 209);
  color: rgb(112, 112, 112);
  font-size: 3rem;
  place-items: center;
  border-radius: 10px;
}
</style>
