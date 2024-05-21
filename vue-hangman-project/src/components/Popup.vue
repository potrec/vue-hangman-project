<template>
    <div v-if="finalMessage" class="popup-container" id="popup-container">
        <div class="popup">
            <h2>{{ finalMessage }}</h2>
            <h3 v-show="status === 'lost'">...the word was: {{  word }}</h3>
            <button @click="reset">Play again</button>
        </div>
    </div>
</template>
<script>
import { computed } from 'vue'
export default {
    props: {
        status: {type: String, default: ''},
        word: {type: String, default: ''}
    },
    setup(props, context){
        const finalMessage = computed(() =>
        {
            if(props.status === 'win') return 'Congratulations! You won :)'
            if(props.status === 'lose') return 'You lost :('
            return ''
        })
        const reset = () => context.emit('reset')
        return { finalMessage, reset }
    },
}
</script>