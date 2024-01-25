<template>
    <select v-model="selectSort" @change="changeOption">
        <option 
            style="select" 
            disabled 
            value=""
        >
            Выберите из списка
        </option>
        <option 
            v-for="option in options"
            :key="option.value"
            :value="option.value"
        >{{ option.name }}
        </option>
    </select>
</template>
    
<script>
export default {
    name: 'my-select',
    props: {
        modelValue: {
            type: String,
        },
        options: {
            type: Array,
            default: () => []
        }
    },
    methods: {
        changeOption(event) {
            this.$emit('update:modelValue', event.target.value)
        }
    }
}
</script>
    
<style scoped>
.select {
    border: 1px solid #00a144;
    border-radius: 5px;
}
</style>