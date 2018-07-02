<template>
    <div
        class="container"
    >
        <Field :fields="fields" />
        <Step v-on:generateNewStep="generateNewStep" />
        <Controls />
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