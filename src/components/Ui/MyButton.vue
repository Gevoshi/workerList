<template>
    <button 
        class="btn">
        <slot></slot>
    </button>
</template>

<script>
export default {
    name: 'MyButton'
}
</script>

<style scoped>
    .btn{
        margin-top: 15px;
        align-self: flex-end;
        padding: 10px 15px;
        background: none;
        color: teal;
        border: 2px solid teal;
        border-radius: 12px;
        cursor: pointer;
        transition: 0.3s all ease;
    }

    .btn:hover {
        color: yellowgreen;
        border-color: yellowgreen;
        transition: 0.3s all ease;
    }
</style>