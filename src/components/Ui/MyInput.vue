<template>
    <input 
        class='input'
        :value="modelValue"
        @input="updateInput">
</template>

<script>
export default {
    name: 'MyInput',
    props: {
        modelValue: [String, Number]
    },

    methods: {
        updateInput(event){
            this.$emit('update:modelValue', event.target.value)
        }
    }
}
</script>

<style>
    .input{
        width: 100%;
        border: 2px solid teal;
        padding: 10px 15px;
        margin-top: 15px;
        border-radius: 12px;
    }
</style>