<template>
    <input 
        class="input" 
        type="text" 
        :value="value"
        @input="updateInput"
    >
</template>
    
<script>
export default {
    name:  'my-input',
    props: {
        value: [String, Number]
    },
    methods: {
        updateInput(event) {
            this.$emit('update:value', event.target.value)
        }
    }
}
</script>
    
<style>
.input {
    border: 1px solid #00a144;
    border-radius: 5px;
    padding: 10px;
}
</style>