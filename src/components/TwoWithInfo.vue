<template>
    <div>
        <h1 class="section-heading" v-bind:class="{'hidden' : !completedTextHidden}">Provide Details</h1>
        <div class="progress-bar"></div>
        <div>
            <div class="two-info-questions-1 question-section" v-bind:class="{'hidden' : twoInfoQuestionsOneHidden}">
                <div class="question-wrapper">
                    <label for="companionOne" class="question-label">Companion One First Name</label>
                    <input v-model="companionOne" id="companionOne" class="question-input"/>
                </div>
                <div class="question-wrapper">
                    <label for="companionTwo" class="question-label">Companion Two First Name</label>
                    <input v-model="companionTwo" id="companionTwo" class="question-input"/>
                </div>
                <div class="question-wrapper">
                    <label for="presMember" class="question-label">Your Name</label>
                    <input v-model="presMember" id="presMember" class="question-input"/>
                </div>
                <button @click="showNextQuestion('twoInfoQuestionsOneHidden', 'twoInfoQuestionsTwoHidden')" class="next-question">&#8594;</button>
            </div>
            <div class="two-info-questions-2 question-section" v-bind:class="{'hidden' : twoInfoQuestionsTwoHidden}">
                <div class="question-wrapper">
                    <label for="msOneFirstName" class="question-label">First Sister Assigned First Name</label>
                    <input v-model="msOneFirstName" id="msOneFirstName" class="question-input"/>
                </div>
                <div class="question-wrapper">
                    <label for="msOneLastName" class="question-label">First Sister Assigned Last Name</label>
                    <input v-model="msOneLastName" id="msOneLastName" class="question-input"/>
                </div>
                <button @click="showNextQuestion('twoInfoQuestionsTwoHidden', 'twoInfoQuestionsThreeHidden')" class="next-question">&#8594;</button>
            </div>
            <div class="two-info-questions-3 question-section" v-bind:class="{'hidden' : twoInfoQuestionsThreeHidden}">
                <div class="question-wrapper">
                    <label for="msOneMinisteringType" class="question-label">How {{msOneFirstName}} likes to be ministered to:</label>
                    <input v-model="msOneMinisteringType" id="msOneMinisteringType" class="question-input">
                </div>
                <div class="question-wrapper">
                    <label for="msOneAvailability" class="question-label">{{msOneFirstName}}'s Availability</label>
                    <input v-model="msOneAvailability" id="msOneAvailability" class="question-input">
                </div>
                <div class="question-wrapper">
                    <label for="msOneTreat" class="question-label">{{msOneFirstName}}'s Favorite Treat</label>
                    <input v-model="msOneTreat" id="msOneTreat" class="question-input">
                </div>
                <div class="question-wrapper">
                    <label for="msOneNumber" class="question-label">{{msOneFirstName}}'s Phone #</label>
                    <input v-model="msOneNumber" id="msOneNumber" class="question-input">
                </div>
                <button @click="showNextQuestion('twoInfoQuestionsThreeHidden', 'twoInfoQuestionsFourHidden')" class="next-question">&#8594;</button>
            </div>
            <div class="two-info-questions-4 question-section" v-bind:class="{'hidden' : twoInfoQuestionsFourHidden}">
                <div class="question-wrapper">
                    <label for="msTwoFirstName" class="question-label">Second Sister Assigned First Name</label>
                    <input v-model="msTwoFirstName" id="msTwoFirstName" class="question-input"/>
                </div>
                <div class="question-wrapper">
                    <label for="msTwoLastName" class="question-label">Second Sister Assigned Last Name</label>
                    <input v-model="msTwoLastName" id="msTwoLastName" class="question-input"/>
                </div>

                <button @click="showNextQuestion('twoInfoQuestionsFourHidden', 'twoInfoQuestionsFiveHidden')" class="next-question">&#8594;</button>
            </div>
            <div class="two-info-questions-5 question-section" v-bind:class="{'hidden' : twoInfoQuestionsFiveHidden}">
                <div class="question-wrapper">
                    <label for="msTwoMinisteringType" class="question-label">How {{msTwoFirstName}} likes to be ministered to:</label>
                    <input v-model="msTwoMinisteringType" id="msTwoMinisteringType" class="question-input">
                </div>
                <div class="question-wrapper">
                    <label for="msTwoAvailability" class="question-label">{{msTwoFirstName}}'s Availability</label>
                    <input v-model="msTwoAvailability" id="msTwoAvailability" class="question-input">
                </div>
                <div class="question-wrapper">
                    <label for="msTwoTreat" class="question-label">{{msTwoFirstName}}'s Favorite Treat</label>
                    <input v-model="msTwoTreat" id="msTwoTreat" class="question-input">
                </div>
                <div class="question-wrapper">
                    <label for="msTwoNumber" class="question-label">{{msTwoFirstName}}'s Phone #</label>
                    <input v-model="msTwoNumber" id="msTwoNumber" class="question-input">
                </div>

                <button @click="finishQuestions('twoInfoQuestionsFiveHidden')" class="next-question">&#8594;</button>
            </div>

        </div>

        <div v-bind:class="{'hidden' : completedTextHidden}">
            <h1 class="section-heading">Copy & Paste</h1>
            <p class="text-to-review">Hello {{companionOne}} & {{companionTwo}}!</p>
            <p class="text-to-review">This is {{presMember}} from the ward. :) We as a Relief Society appreciate your willingness to minister to a few sisters in our ward. Their names are {{msOneFirstName}} {{msOneLastName}} & {{msTwoFirstName}} {{msTwoLastName}}. We encourage you to get to know each other as you will be companions, and to get to know these sisters so you can reach out in love to fulfill their needs. Let me know if there is anything I can do to assist you as I am here to offer you support. This is a new assignment so you'll probably need to sync your LDS tools app to see it updated there.</p>
            <p class="text-to-review">In the surveys we handed out, Sister {{msOneLastName}} said that she enjoys {{msOneMinisteringType}}. She's available {{msOneAvailability}}. Her favorite treats are {{msOneTreat}}.</p>
            <p class="text-to-review">Sister {{msTwoLastName}} enjoys {{msTwoMinisteringType}}. She's available {{msTwoAvailability}}. Her favorite treat is {{msTwoTreat}}.</p>
            <p class="text-to-review">We love you Sisters and know that you will be of great help to {{msOneFirstName}} & {{msTwoFirstName}}!</p>
            <p class="text-to-review">
                {{msOneFirstName}}'s number: {{msOneNumber}}
                {{msTwoFirstName}}'s number: {{msTwoNumber}}
            </p>
            <div>
<textarea id="text" class="text-to-copy">
Hello {{companionOne}} & {{companionTwo}}!

This is {{presMember}} from the ward. :) We as a Relief Society appreciate your willingness to minister to a few sisters in our ward. Their names are {{msOneFirstName}} {{msOneLastName}} & {{msTwoFirstName}} {{msTwoLastName}}. We encourage you to get to know each other as you will be companions, and to get to know these sisters so you can reach out in love to fulfill their needs. Let me know if there is anything I can do to assist you as I am here to offer you support. This is a new assignment so you'll probably need to sync your LDS tools app to see it updated there.

In the surveys we handed out, Sister {{msOneLastName}} said that she enjoys {{msOneMinisteringType}}. She's available {{msOneAvailability}}. Her favorite treats are {{msOneTreat}}.

Sister {{msTwoLastName}} enjoys {{msTwoMinisteringType}}. She's available {{msTwoAvailability}}. Her favorite treat is {{msTwoTreat}}.

We love you Sisters and know that you will be of great help to {{msOneFirstName}} & {{msTwoFirstName}}!

{{msOneFirstName}}'s number: {{msOneNumber}}

{{msTwoFirstName}}'s number: {{msTwoNumber}}
</textarea>
            </div>
            <button @click="copyText()" class="copy-button">Copy Text</button>
            <button v-on:click="reset(); $emit('start-again')" class="start-again-button">Start Again</button>
        </div>


    </div>
</template>

<script>
    export default {
        name: 'TwoWithInfo',
        props: {
            msg: String
        },
        data() {
            return {
                companionOne : '',
                companionTwo : '',
                presMember : '',
                msOneFirstName : '',
                msOneLastName : '',
                msOneMinisteringType : '',
                msOneAvailability : '',
                msOneTreat : '',
                msOneNumber : '',
                msTwoFirstName : '',
                msTwoLastName : '',
                msTwoMinisteringType : '',
                msTwoAvailability : '',
                msTwoTreat : '',
                msTwoNumber : '',
                text : '',
                twoInfoQuestionsOneHidden : false,
                twoInfoQuestionsTwoHidden : true,
                twoInfoQuestionsThreeHidden : true,
                twoInfoQuestionsFourHidden : true,
                twoInfoQuestionsFiveHidden : true,
                completedTextHidden : true
            }

        },
        methods : {
            copyText() {
                let textToCopy = document.getElementById('text');
                textToCopy.select();
                document.execCommand("copy");
                alert('text copied');
            },

            showNextQuestion(currentQuestionSection, nextSection) {
                this[currentQuestionSection] = !this[currentQuestionSection];
                this[nextSection] = !this[nextSection];
            },

            finishQuestions(currentQuestionSection) {
                this[currentQuestionSection] = !this[currentQuestionSection];
                this.completedTextHidden = false;
            },

            reset() {
                this.companionOne = '';
                this.companionTwo = '';
                this.presMember = '';
                this.msOneFirstName = '';
                this.msOneLastName = '';
                this.msOneMinisteringType = '';
                this.msOneAvailability = '';
                this.msOneTreat = '';
                this.msOneNumber = '';
                this.msTwoFirstName = '';
                this.msTwoLastName = '';
                this.msTwoMinisteringType = '';
                this.msTwoAvailability = '';
                this.msTwoTreat = '';
                this.msTwoNumber = '';
                this.text = '';
                this.twoInfoQuestionsOneHidden = false;
                this.twoInfoQuestionsTwoHidden = true;
                this.twoInfoQuestionsThreeHidden = true;
                this.twoInfoQuestionsFourHidden = true;
                this.twoInfoQuestionsFiveHidden = true;
                this.completedTextHidden = true;
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h3 {
        margin: 40px 0 0;
    }
    ul {
        list-style-type: none;
        padding: 0;
    }
    li {
        margin: 0 10px;
    }
    a {
        color: #42b983;
    }

    .question-section {
        display: flex;
        flex-direction: column;
    }


    .question-wrapper {
        display: flex;
        flex-direction: column;
        margin-bottom: 2rem;
    }

    .question-label {
        text-transform: uppercase;
        font-weight: 500;
        font-size: .7rem;
    }

    .question-input {
        border: solid 1px #000;
        padding: .5rem;
        font-size: 1.2rem;
        font-family: 'Montserrat', Helvetica, Arial, sans-serif;
        color: #343085;
    }

    .next-question {
        font-size: 2rem;
        text-align: right;
        background: #fff;
        border: none;
        transition: all .3s ease-in-out;
    }

    .next-question:hover {
        cursor: pointer;
        transform: translateX(10px);
        transition: all .3s ease-in-out;
    }

    .hidden {
        display: none;
    }

    .text-to-review {
        font-size: .8rem;
    }

    .text-to-copy {
        opacity: 0;
        transform: translateX(1000px);
    }

    .copy-button {
        color: #fff;
        font-size: 1.2rem;
        font-weight: 600;
        font-family: 'Montserrat', Helvetica, Arial, sans-serif;
        text-transform: uppercase;
        background: #343085;
        width: 95%;
        padding: 1rem;
        border: none;
        transition: all .3s ease-in-out;
    }

    .copy-button:hover, .start-again-button:hover {
        cursor: pointer;
        transform: scale(1.1);
        transition: all .3s ease-in-out;
    }

    .start-again-button {
        font-size: 1.2rem;
        font-weight: 600;
        font-family: 'Montserrat', Helvetica, Arial, sans-serif;
        text-transform: uppercase;
        width: 95%;
        padding: 1rem;
        border: 2px solid #000;
        background: #fff;
        margin-top: 2rem;
    }
</style>
