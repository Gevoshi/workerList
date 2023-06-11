<template>
    <div class="dialog" v-if="show" @click="hideDialog">
        <div @click.stop class="dialogContent">
            <slot></slot>
        </div>
    </div>
</template>

<script>
export default {
    name: 'MyDialog',
    props: {
        show: {
            type: Boolean,
            default: false
        }
    },

    methods: {
        hideDialog(){
            this.$emit('update:show', false)
        }
    }
}
</script>

<style>
    .dialog{
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        position: fixed;
        background: rgba(0, 0, 0, 0.5);
        display: flex;
    }

    .dialogContent{
        margin: auto;
        background: white;
        border-radius: 12px;
        padding: 20px;
    }
</style>