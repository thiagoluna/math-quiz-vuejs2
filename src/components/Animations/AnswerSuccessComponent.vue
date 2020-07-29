<template>
    <div class="alert alert-success text-center">
        <h2 v-text="title"></h2>
        <p>Correct Answer! \o/</p>

        <button @click="nextQuestion" class="btn btn-success">Next Question</button>
    </div>
</template>

<script>
    export default {
        name: "AnswerSuccessComponent",
        data () {
            return {
                title: 'Success'
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
    .success {
        border: 2px solid green;
        padding: 10px;
    }
</style>