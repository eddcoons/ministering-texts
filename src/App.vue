<template>
  <div id="app">
    <!--<img alt="Vue logo" src="./assets/logo.png">-->
    <!--<HelloWorld msg="Welcome to Your Vue.js App"/>-->
    <div v-bind:class="{'hidden' : optionSelected}">
        <h1 class="section-heading">Choose Your Scenario</h1>
        <div class="option-wrapper">
            <h4 class="option-heading">Two Ministering Sisters with Two Sisters Assigned to Them</h4>
            <ul class="options">
                <li class="option" @click="optionSelected = !optionSelected">Have Survey Info for Both</li>
                <li class="option">Have Survey Info for One Sister</li>
                <li class="option">Have Survey Info for Neither</li>
            </ul>
        </div>

    </div>

    <TwoWithInfo v-bind:class="{'hidden' : !optionSelected}"/>
    <button v-bind:class="{'hidden' : !optionSelected}" @click="optionSelected = !optionSelected">Done</button>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import TwoWithInfo from './components/TwoWithInfo'

export default {
  name: 'app',
  components: {
    HelloWorld,
    TwoWithInfo
  },
  data() {
    return {
        optionSelected: false
    }

  }
}
</script>

<style>
#app {
  font-family: 'Montserrat', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
  padding: 0 1rem;
}

.section-heading {
    color: #343085;
    text-transform: uppercase;
    font-size: 1.8rem;
}

.option-heading {
    color: #ffffff;
    background: #84b8b9;
    padding: .5rem;
    font-weight: 500;
}

.options {
    list-style: none;
    padding: 0;
}

.option {
    border: solid 2px #84b8b9;
    margin: 0 0 1rem 0;
    padding: .5rem;
    font-size: .8rem;
}

.option:hover, .option:focus {
    background: #84b8b9;
    color: #fff;
}

.hidden {
    display: none;
}
</style>
