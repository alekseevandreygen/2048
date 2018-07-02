<template>
    <div class="step-container">
        <button
            @click="generateNewStep"
        >
            Создать новый шаг
        </button>
    </div>
</template>>

<script>
module.exports = {
    methods: {
        generateNewStep: function() {
            let step = {
                x: Math.floor(Math.random() * 4),
                y: Math.floor(Math.random() * 4),
            }
            this.$emit('generateNewStep', step);
        }
    },
}
</script>

<style>
    .step-container {
        text-align: center;
        margin: 20px 0;
    }
</style>