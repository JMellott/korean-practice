<template>
    <div class="number-practice">
      <h1>Korean Number Practice</h1>
      <div v-if="!practicing">
        <h2>Enter maximum number you would like to practice up to.</h2>
        <input v-model="maximumNumber" type="number" id="maximum" name="maximum"/>
        <button @click="startPractice">Start</button>
      </div>
      <div v-else>
        <h2>{{ currentNumber }}</h2>
        <button v-if="!revealAnswer" @click="revealAnswer = true">Reveal Answer</button>
        <div v-else>
            {{ numToKorean(currentNumber, 'lingual') }}
            <button @click="generateNextNumber">Next</button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import { numToKorean } from 'num-to-korean'
  export default {
    name: 'NumberPractice',
    data() {
        return {
            practicing: false,
            maximumNumber: null,
            currentNumber: null,
            revealAnswer: false,
            numToKorean,
        }
    },
    methods: {
        startPractice() {
            this.practicing = true
            this.generateNumber()
        },
        generateNextNumber() {
            this.revealAnswer = false
            this.generateNumber()
        },
        generateNumber() {
            this.currentNumber = Math.floor(Math.random() * this.maximumNumber)
        }
    }
  }
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
  