<template>
    <div class="container">
        <h2 v-text="title"></h2>

        <div class="row">
            <div class="custom-width">
                <transition name="effect" mode="out-in">
                    <!--<app-question @changeMode="changeMode"></app-question>-->
                    <component
                            :is="mode"
                            @changeMode="changeMode">
                    </component>
                </transition>
            </div>
        </div>
    </div>
</template>

<script>
    import Question from "./Question";
    import AnswerSuccessComponent from "./AnswerSuccessComponent";
    import AnswerErrorComponent from "./AnswerErrorComponent";

    export default {
        name: "Quiz",
        data () {
            return {
                title: 'Math Quiz',
                mode: 'app-question'
            }
        },
        methods: {
            changeMode (mode) {
                this.mode = mode
            }
        },
        components: {
            AnswerSuccessComponent,
            AnswerErrorComponent,
            'app-question': Question
        }
    }
</script>

<style scoped>
    .custom-width {
        max-width: 500px;
        margin: auto;
    }

    .effect-enter-active {
        animation: effect-in 1s;
    }

    .effect-leave-active {
        animation: effect-out 1s;
    }

    @keyframes effect-out {
        from {
            transform: rotateY(0deg);
        }
        to {
            transform: rotateY(90deg);
        }
    }

    @keyframes effect-in {
        from {
            transform: rotateY(90deg);
        }
        to {
            transform: rotateY(0deg);
        }
    }
</style>