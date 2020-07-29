<template>
    <div class="alert alert-danger text-center">
        <h2 v-text="title"></h2>
        <p>Wrong Answer!</p>

        <button @click="nextQuestion" class="btn btn-danger">Next Question</button>
    </div>
</template>

<script>
    export default {
        name: "AnswerErrorComponent",
        data () {
            return {
                title: 'Ops'
            }
        },
        methods: {
            nextQuestion () {
                let mode= 'app-question'
                this.$emit('changeMode', mode)
            }
        }
    }
</script>

<style scoped>
    .error {
        border: 2px solid red;
        padding: 10px;
    }
</style>