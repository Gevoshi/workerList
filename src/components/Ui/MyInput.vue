<template>
    <div>
        <input 
        class='input'
        :value="modelValue"
        v-bind="$attrs"
        @input="updateInput"
        
        @checkInputValid="checkInputValid">
        <my-error-message v-show="error" :errorMessage="errorMessage" />
    </div>
</template>

<script>

export default {
    name: 'MyInput',
    props: {
        modelValue: [String, Number],
        errorMessage: {
            type: String,
            required: true
        },
        error: {
            type: Boolean,
            required: true
        },

    },

    methods: {
        updateInput(event){
            this.$emit('update:modelValue', event.target.value)
        },
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