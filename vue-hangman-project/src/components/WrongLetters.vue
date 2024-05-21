<template>
    <div class="">
        <p v-show="wrongLetters.length > 0"></p>
        <span v-for="(letter, i) in wrongLetters" :key="letter">
            {{ letter }}
            {{ i === wrongLetters.length - 1 ? '' : ', '}}
        </span>
    </div>

</template>

<script>
export default {
    props: {
        wrongLetters: { type: Array, default: () => []}
    }
}
</script>