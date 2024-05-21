<template>
    <div class="wrong-letters-container">
        <div class="wrong-letters">
            <p v-show="wrongLetters.length > 0">Wrong</p>
            <span v-for="(letter, i) in wrongLetters" :key="letter">
                {{ letter }}
                {{ i === wrongLetters.length - 1 ? '' : ', '}}
            </span>
        </div>
        <div class="good-letters">
            <p v-show="correctLetters.length > 0">Good</p>
            <span v-for="(letter, i) in correctLetters" :key="letter">
                {{ letter }}
                {{ i === correctLetters.length - 1 ? '' : ', '}}
            </span>
        </div>
    </div>

</template>

<script>
export default {
    props: {
        wrongLetters: { type: Array, default: () => []},
        correctLetters: { type: Array, default: () => []},
    }
}
</script>