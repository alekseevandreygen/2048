<template>
    <div class="controls-container">
        <div class="row">
            <div 
                class="control"
                @click="upEvent"
            >
                &uarr;
            </div>
        </div>

        <div class="row">
            <div 
                class="control"
                @click="leftEvent"
            >
                &larr;
            </div>
            <div 
                class="control"
                @click="rightEvent"
            >
                &rarr;
            </div>
        </div>

        <div class="row">
            <div 
                class="control"
                @click="downEvent"
            >
                &darr;
            </div>
        </div>
    </div>
</template>

<script>
module.exports = {
    methods: {
        upEvent: function() {
            
        },
        leftEvent: function() {
            
        },
        rightEvent: function() {
            
        },
        downEvent: function() {
            
        },
    }
}
</script>

<style>
    .controls-container {
        cursor: pointer;
    }
    .row {
        display: flex;
    }
    .control {
        margin: 0 auto;
    }
</style>