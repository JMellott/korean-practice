<template>
    <div class="number-practice">
      <h1>Korean Clock Practice</h1>
      <div>
        <h2>{{ currentTime }}</h2>
        <button v-if="!revealAnswer" @click="revealAnswer = true">Reveal Answer</button>
        <div v-else>
            {{ clockToKorean(currentTime) }}
            <button @click="generateTime">Next</button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import { numToKorean } from 'num-to-korean'
  import { nativeKoreanNumbers } from '@/utils/time'
  export default {
    name: 'ClockPractice',
    data() {
        return {
            currentTime: null,
            revealAnswer: false,
            currentHour: 0,
            currentMinute: 0,
            numToKorean,
            nativeKoreanNumbers,
        }
    },
    mounted() {
        this.generateTime()
    },
    methods: {
        generateTime() {
            this.revealAnswer = false
            let tempHour = Math.floor((Math.random() * 12) + 1)
            const hour = tempHour > 12 ? 12 : tempHour
            const hourString = hour > 9 ? hour : `0${hour}`

            let tempMinute = Math.floor((Math.random() * 59) + 1)
            const minute = tempMinute > 59 ? 59 : tempMinute
            const minuteString = minute > 9 ? minute : `0${minute}`

            this.currentTime = `${hourString}:${minuteString}`
            this.currentHour = hour
            this.currentMinute = minute
        },
        clockToKorean() {
            const hourPart = nativeKoreanNumbers[this.currentHour]
            const minutePart = numToKorean(this.currentMinute, 'lingual')
            return `${hourPart}시 ${minutePart}분`
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
  