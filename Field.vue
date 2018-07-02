<template >
    <div>
        <div
            :fields="fields"
            v-for="(row, index) in fields"
            :key="index"
            class="field-container"
        >
            <div
                @click="checking(column)"
                :fields="fields"
                v-for="(column, _index) in row"
                :key="_index"
                class="field-item"
            >
                {{ column }}
            </div>
        </div>
    </div>
</template>

<script>
    module.exports = {
        props: ['fields'],
        methods: {
            checking: function(msg) {
                console.log(msg)
            }
        }
    }
</script>

<style>

    body {
        font-family: Arial, Helvetica, sans-serif
    }
    
    .field-container {
        border: 1px solid grey;
        display: flex;
    }

    .field-container div {
        border-left: 1px solid grey;
        flex: 1;
    }

    .field-container div:nth-child(odd) {
        border-right: 1px solid grey;
        flex: 1;
    }

    .field-item {
        padding: 10px;
    }

</style>