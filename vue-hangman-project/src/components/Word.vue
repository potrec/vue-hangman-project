<template>
    <div class="word">
        <div v-for="(letter,i) in letters" class="letter" :class="['letter', letter === ' ' ? '' : 'letter-border']">
            <span v-if="correctLetters.includes(letter)">{{ letter }}</span>
        </div>
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

