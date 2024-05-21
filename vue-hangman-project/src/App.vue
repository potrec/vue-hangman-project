<template>
    <Header/>
    <div class= "game-container">
      <Figure :wrongLetters="wrongLetters"/>
      <WrongLetters :wrongLetters="wrongLetters"/>
      <Word :letters="letters" :correct-letters="correctLetters"/>
    </div>
    <Popup :status="status" :word="word" @reset="reset"/>
    <Notification :show="notification"/>
</template>

<script>
import { ref, computed, watch } from 'vue'

import onkeydown from './assets/onKeydown.js'

import Figure from './components/Figure.vue';
import Header from './components/Header.vue';
import Word from './components/Word.vue';
import WrongLetters from './components/WrongLetters.vue';
import Notification from './components/Notification.vue';
import Popup from './components/Popup.vue';

const words = ['test','test2','test3']
const randomWord = () => words[Math.floor(Math.random() * words.length)]

export default {
  components: {
    Header,
    Figure,
    Word,
    WrongLetters,
    Notification,
    Popup
  },
  setup() {
    const word = ref(randomWord())
    const guessedLetters = ref([])

    const letters = computed(() => word.value.split(''))
    const wrongLetters = computed(() => guessedLetters.value.filter(l => !letters.value.includes(l)))
    const correctLetters = computed(() => guessedLetters.value.filter(l => letters.value.includes(l)))

    const status = computed(() => {
      if(wrongLetters.value.length === 6) return 'lose'
      if(letters.value.every(l => correctLetters.value.includes(l))) return 'win'
      return ''
    })

    const reset = () => {
      guessedLetters.value = []
      word.value = randomWord()
    }

    const notification = ref(false)
    const showNotification = () => {
      console.log("notification")
      notification.value = true
      setTimeout(() => (notification.value = false), 2000)
    }

    onkeydown(event => {
        const letter = event.key.toLowerCase()
        if(event.keyCode < 65 && event.keyCode > 90) return
        if(status.value) return
        if(guessedLetters.value.includes(letter)) {
          showNotification()
          return
        }
        guessedLetters.value.push(letter)
    })

    return {
      letters,
      word,
      wrongLetters,
      correctLetters,
      guessedLetters,
      notification,
      status,
      reset
    }
  }
}
</script>

