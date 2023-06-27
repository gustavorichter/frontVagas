<template>
    <div class="toggle" :class="{ 'checked': checked }" @click="toggle">
        <div class="toggle-track"></div>
        <div class="toggle-thumb"></div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            checked: false,
        };
    },
    methods: {
        toggle() {
            this.checked = !this.checked;
        },
    },
};
</script>

<style scoped>
.toggle {
    position: relative;
    width: 50px;
    height: 24px;
    background-color: #ccc;
    border-radius: 12px;
    cursor: pointer;
    transition: background-color 0.2s ease-in-out;
}

.toggle-track {
    position: absolute;
    top: 50%;
    left: 2px;
    width: 20px;
    height: 20px;
    background-color: #fff;
    transform: translate(0, -50%);
    border-radius: 50%;
    transition: transform 0.2s ease-in-out;
}

.toggle-thumb {
    position: absolute;
    top: 2px;
    left: 2px;
    width: 20px;
    height: 20px;
    background-color: #999;
    border-radius: 50%;
    transition: transform 0.2s ease-in-out;
}

.checked {
    background-color: #6c63ff;
}

.checked .toggle-track {
    transform: translate(100%, -50%);
}

.checked .toggle-thumb {
    transform: translate(20px, -0%)
}
</style>