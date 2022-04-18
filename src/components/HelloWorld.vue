<template>
  <div class="container flex justify-center justify-items-center">
    <Question1 v-show="Question1Component.isActive" v-on:valid="stepTwo" />
    <Question2 v-show="Question2Component.isActive" v-on:valid="stepThree" />
  </div>
</template>

<script>
import Question1 from "./Question1";
import Question2 from "./Question2";

export default {
  name: "HelloWorld",
  components: { Question1, Question2 },
  data: function () {
    return {
      Question1Component: {
        isActive: true,
      },
      Question2Component: {
        isActive: false,
      },
    };
  },
  props: {
    msg: String,
  },
  methods: {
    stepTwo() {
      this.Question1Component.isActive = false;
      this.Question2Component.isActive = true;
    },
    stepThree() {
      this.Question2Component.isActive = false;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
