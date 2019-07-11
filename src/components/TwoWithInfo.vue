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
                    <label>Second Sister Assigned First Name</label>
                    <input v-model="msTwoFirstName"/>
                    <label>Second Sister Assigned First Name</label>
                    <input v-model="msTwoLastName"/>
                </div>

                <button @click="showNextQuestion('twoInfoQuestionsFourHidden', 'twoInfoQuestionsFiveHidden')">Next</button>
            </div>
            <div class="two-info-questions-5" v-bind:class="{'hidden' : twoInfoQuestionsFiveHidden}">
                <label>How {{msTwoFirstName}} likes to be ministered to:</label><input v-model="msTwoMinisteringType">
                <label>{{msTwoFirstName}}'s Availability</label><input v-model="msTwoAvailability">
                <label>{{msTwoFirstName}}'s Favorite Treat</label><input v-model="msTwoTreat">
                <label>{{msTwoFirstName}}'s Phone #</label><input v-model="msTwoNumber">
                <button @click="finishQuestions('twoInfoQuestionsFiveHidden')">Finish!</button>
            </div>

        </div>

        <div v-bind:class="{'hidden' : completedTextHidden}">
            <h1 class="section-heading">Copy & Paste</h1>
            <p>Hello {{companionOne}} & {{companionTwo}}!</p>
            <p>This is {{presMember}} from the ward. :) We as a Relief Society appreciate your willingness to minister to a few sisters in our ward. Their names are {{msOneFirstName}} {{msOneLastName}} & {{msTwoFirstName}} {{msTwoLastName}}. We encourage you to get to know each other as you will be companions, and to get to know these sisters so you can reach out in love to fulfill their needs. Let me know if there is anything I can do to assist you as I am here to offer you support. This is a new assignment so you\'ll probably need to sync your LDS tools app to see it updated there.</p>
            <p>In the surveys we handed out, Sister {{msOneLastName}} said that she enjoys {{msOneMinisteringType}}. She's available {{msOneAvailability}}. Her favorite treats are {{msOneTreat}}.</p>
            <p>Sister {{msTwoLastName}} enjoys {{msTwoMinisteringType}}. She's available {{msTwoAvailability}}. Her favorite treat is {{msTwoTreat}}.</p>
            <p>We love you Sisters and know that you will be of great help to {{msOneFirstName}} & {{msTwoFirstName}}!</p>
            <p>
                {{msOneFirstName}}'s number: {{msOneNumber}}
                {{msTwoFirstName}}'s number: {{msTwoNumber}}
            </p>
            <button @click="copyText()">Copy Text</button>
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
                console.log(textToCopy);
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
    }

    .hidden {
        display: none;
    }
</style>
