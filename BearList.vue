<template>
    <ul>
        <li 
            v-for="(bear, index) in bears"
            @click="click(bear, $event)"
            :key="index"
        >
            {{bear}}
        </li>
    </ul>
</template>

<script>
module.exports = {
    props: ['bears'],
    methods: {
        click: function(bear, e) {
            const msg = bear + ' has growled.'
            this.$emit('click', msg, e)
        }
    }
}
</script>