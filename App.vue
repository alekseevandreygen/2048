<template>
    <div
        class="container"
    >
        <Field :fields="fields" />
        <Step 
            v-on:generateNewStep="generateNewStep" 
        />
        <Controls 
        />
        <div @click="leftEvent">dsds</div>
    </div>
</template>

<script>

const Field = require('./Field.vue');
const Step = require('./Step.vue');
const Controls = require('./Controls.vue');

module.exports = {
    data: function() {
        return {
            fields: [
                [ 0, 0, 0, 0 ],
                [ 0, 0, 0, 0 ],
                [ 0, 0, 0, 0 ],
                [ 0, 0, 0, 0 ],
            ]
        }
    },
    methods: {
        generateNewStep: function(generateNewStep) {
            this.$set(this.fields[generateNewStep.x], generateNewStep.y, 2);
        },
        leftEvent: function() {
            let oldState = this.fields;
            let newState = new Array();
            for (let i = 0; i < oldState.length; i++) {
                newState[i] = new Array();
                for (let j = oldState.length-1; j >= 0; j--) {

                    if ( oldState[i][j] === 0 &&
                        oldState[i][j-1] === 0 &&
                        oldState[i][j-2] === 0 &&
                        oldState[i][j-3] === 0
                    ) {
                        newState[i][j-3] = 0;
                        newState[i][j-2] = 0;
                        newState[i][j-1] = 0;
                        newState[i][j] = 0;
                    } else if (
                        oldState[i][j] === 0 &&
                        oldState[i][j-1] === 0 &&
                        oldState[i][j-2] === 0
                    ) {
                        newState[i][j-3] = 0;
                        newState[i][j-2] = 0;
                        newState[i][j-1] = 0;
                        newState[i][j] = oldState[i][j-3];
                    } else if (
                        oldState[i][j] === 0 &&
                        oldState[i][j-1] === 0
                    ) {
                        newState[i][j-3] = 0;
                        newState[i][j-2] = 0;
                        newState[i][j-1] = 0;
                        newState[i][j] = oldState[i][j-3];
                    } else if (
                        oldState[i][j] === 0
                    ) {
                        newState[i][j-3] = 0;
                        newState[i][j-2] = 0;
                        newState[i][j-1] = 0;
                        newState[i][j] = oldState[i][j-1];
                    } else if (
                        oldState[i][j-1] === 0
                    ) {
                        newState[i][j-3] = 0;
                        newState[i][j-2] = oldState[i][j-3];
                        newState[i][j-1] = oldState[i][j-2];
                        newState[i][j] = oldState[i][j];
                    } else if (
                        oldState[i][j-2] === 0
                    ) {
                        newState[i][j-3] = 0;
                        newState[i][j-2] = oldState[i][j-3];
                        newState[i][j-1] = oldState[i][j-1];
                        newState[i][j] = oldState[i][j];
                    } else if (
                        oldState[i][j-3] === 0
                    ) {
                        newState[i][j-3] = 0;
                        newState[i][j-2] = oldState[i][j-2];
                        newState[i][j-1] = oldState[i][j-1];
                        newState[i][j] = oldState[i][j];
                    } else if (
                        oldState[i][j] === 0 &&
                        oldState[i][j-2] === 0
                    ) {
                        newState[i][j-3] = 0;
                        newState[i][j-2] = oldState[i][j-3];
                        newState[i][j-1] = oldState[i][j-2];
                        newState[i][j] = oldState[i][j-1];
                    } else if (
                        oldState[i][j-1] === 0 &&
                        oldState[i][j-3] === 0
                    ) {
                        newState[i][j-3] = 0;
                        newState[i][j-2] = 0;
                        newState[i][j-1] = oldState[i][j-2];
                        newState[i][j] = oldState[i][j];
                    } else {
                        newState[i][j-3] = oldState[i][j-3];
                        newState[i][j-2] = oldState[i][j-2];
                        newState[i][j-1] = oldState[i][j-1];
                        newState[i][j] = oldState[i][j];
                    }
                    break;
                }

            }
            this.$set(this.fields, newState);
            console.log(oldState, newState);
        }
    },
    components: {
        Field: Field,
        Step: Step,
        Controls: Controls,
    }
}
</script>

<style>

    .container {
        max-width: 600px;
        margin: 100px auto 0 auto;
    }  

</style>