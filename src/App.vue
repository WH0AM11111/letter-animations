<template>
  <h1>I am a</h1>
  <div class="animation-letter-inputs">
    <h1></h1>
  </div>
</template>
 
<script>
import { onMounted } from "vue";

export default {
  name: "App",
  setup() {
    onMounted(() => {
      let letterDelay = 0;
      let add = 5750;
      function animationName() {
        function letterAnimation(word, delay) {
          let addWordDelay = delay;
          let flashTestDelay = 0;
          let removeWordDelay = 0;

          for (let i = 0; i < word.length; i++) {
            addWordDelay += 100;
            let el = document.querySelector(".animation-letter-inputs h1");
            const chars = word.split("");
            console.log(chars);
            setTimeout(function () {
              el.innerHTML += chars[i];
            }, addWordDelay);
          }

          flashTestDelay = addWordDelay;

          function flashTest(value) {
            for (let i = 0; i < 1; i++) {
              let el = document.querySelector(".animation-letter-inputs h1");
              flashTestDelay += 500;
              if (!value) {
                setTimeout(function () {
                  el.innerHTML = el.innerHTML.replace("_", "");
                }, flashTestDelay);
              } else {
                setTimeout(function () {
                  el.innerHTML += "_";
                }, flashTestDelay);
              }
            }
          }

          removeWordDelay = flashTestDelay + 3300;

          for (let i = word.length; i > -1; i--) {
            removeWordDelay += 150;
            let el = document.querySelector(".animation-letter-inputs h1");
            setTimeout(function () {
              el.innerHTML = word.substr(0, i);
            }, removeWordDelay);
          }

          flashTest(true);
          flashTest(false);
          flashTest(true);
          flashTest(false);
          flashTest(true);
          flashTest(false);
        }

        letterAnimation("DEVELOPER", 0);
        letterAnimation("DESIGNER", letterDelay += add);
        letterAnimation("STUDENT", letterDelay += add);
        letterAnimation("ENGINEER", letterDelay += add);
      }

      animationName();
      setInterval(animationName, letterDelay + 5750);
    });
  },
};
</script>
 
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.animation-letters-1,
.animation-letters-2,
.animation-letters-3 {
  display: flex;
  justify-content: center;
  align-items: center;
}
.letter {
  display: none;
}
</style>