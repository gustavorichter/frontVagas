<template>
    <button @click="handleClick" class="button-component">
        <slot></slot>
    </button>
</template>

<script>
export default {
    name: 'Button',
    methods: {
        handleClick() {
            this.$emit('click');
        },
    },
};
</script>

<style scoped>
.button-component {
    /* Estilos do componente de botão */
}
</style>