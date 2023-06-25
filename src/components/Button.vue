<template>
    <button @click="handleClick" :class="['button', variantClass]">
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
    props: {
        variant: {
            type: String,
            default: 'default'
        }
    },
    computed: {
        variantClass() {
            if (this.variant === 'primary') {
                return 'button-primary';
            } else if (this.variant === 'secondary') {
                return 'button-secondary';
            } else if (this.variant === 'accent') {
                return 'button-accent';
            } else {
                return ''; // classe padrão para a variante 'default'
            }
        }
    }
};
</script>