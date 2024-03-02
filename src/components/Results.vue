<template>
  <div class="result" @click="closeResult">
    <p class="text">{{ message }}</p>
  </div>
</template>

<script>
export default {
  props: ['message'],
  
  data(){
    return{
    }
  },

  methods: {
    closeResult() {
      this.$emit("closeResult");
    },
/*
    finalMessage(){
      if (isNumber(ToNumber(this.message))) {
        return "Your result is: " + this.message + " seconds"
      } 
      else{
        return this.message
      }
    }*/
  },
  
};

</script>

<style scoped>
.result {
  width: 100%;
  height: 300px;
  outline: auto;
  background-color: rgb(199, 197, 197);
  align-content: center;
  line-height: 300px;
  border-radius: 5%;
}

.result .text {
  width: 100%;
  height: 100%;
  font-style: italic;
  text-align: center;
  font-size: 30px;
  color: rgb(0, 0, 0);
  text-underline-position: below;
}
</style>
