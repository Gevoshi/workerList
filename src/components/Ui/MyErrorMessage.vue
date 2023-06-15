<template>
    <div
        class="errorMessage">
        {{ errorMessage }}
    </div>
</template>

<script>
export default {
    name: 'MyErrorMessage',
    props: {
        errorMessage: {
            type: String,
            required: true
        }
    }
}
</script>

<style scoped>
    .errorMessage{
        color: brown;
        font-size: 20px;
    }
</style>