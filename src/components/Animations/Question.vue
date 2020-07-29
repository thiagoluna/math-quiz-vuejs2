<template>
    <div class="card">
        <div class="card-header">
            <h2 v-text="question"></h2>
        </div>

        <div class="card-body row justify-content-center">
            <form @submit.prevent="checkResult" class="form form-inline">
                <input type="text" placeholder="Answer here" v-model="answer" class="form-control">
                <button type="submit" class="btn btn-primary btn-sm ml-2">Answer</button>
            </form>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Question",
        data () {
            return {
                title: 'Quiz',
                question: 'Loading question...',
                result: 0,
                answer: ''
            }
        },
        created() {
            this.generateQuestion()
        },
        methods: {
            generateQuestion () {
                let number1 = this.generateRandomNumber(1, 100)
                let number2 = this.generateRandomNumber(1, 100)

                this.result = number1 + number2

                this.question = `What is the result of ${number1} + ${number2}?`
            },
            generateRandomNumber (min, max) {
                return Math.round(Math.random() * (max - min)) + min
            },
            checkResult () {
                let mode = 'answer-error-component'
                if (this.answer == this.result)
                    mode = 'answer-success-component'
                this.$emit('changeMode', mode)
            }
        }
    }
</script>

<style scoped>
    .text-center {
        text-align: center;
        align-content: center;
    }
</style>