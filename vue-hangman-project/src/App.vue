<script>
import Figure from './components/Figure.vue';
import Header from './components/Header.vue';
import Word from './components/Word.vue';
import WrongLetters from './components/WrongLetters.vue';
export default {
  components: {
    Header,
    Figure,
    Word,
    WrongLetters,
  }
}
</script>
<template>
  <div class= "main">
    <Header/>
    <Figure/>
    <div class= "letters-box">
      <Word/>
      <WrongLetters/>
    </div>
  </div>
</template>

