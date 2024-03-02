<template>
  <div class="block" @click="closeBlock">
    <p class="text">{{ "Click to stop" }}</p>
  </div>
</template>

<script>
export default {

  data(){
    return{
      clickEnd: 0,
    }
  },

  methods: {
    closeBlock() {
      this.clickEnd = performance.now();
      this.$emit("close", this.clickEnd);
    },
  },
};
</script>

<style scoped>
.block {
  width: 100%;
  height: 300px;
  outline: auto;
  background-color: rgb(163, 0, 0);
  align-content: center;
  line-height: 300px;
  border-radius: 5%;
}

.block .text {
  width: 100%;
  height: 100%;
  font-style: italic;
  text-align: center;
  font-size: 40px;
  color: rgb(255, 255, 255);
  text-underline-position: below;
}
</style>
