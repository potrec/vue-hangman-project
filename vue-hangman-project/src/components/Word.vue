<template>
    <div class="word">
        <span v-for="(letter, i) in wrongLetters" :key="letter">
            {{ correctLetters.includes(letter) ? letter : ''}}
        </span>
    </div>
</template>

<script>
export default {
    props: {
        letters: { type: Array, default: () => []},
        correctLetters: { type: Array, default: () => []}
    }
}
</script>