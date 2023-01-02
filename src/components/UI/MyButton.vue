<template>
    <button>
        <slot></slot>
    </button>
</template>

<script>
export default {
    name: 'my-button'
}
</script>

<style scoped>
button {
    padding: 8px 20px;
    color: #fff;
    background: teal;
    border: 2px solid teal;
    cursor: pointer;
    transition: all 0.2s;
}

button:hover {
    background: rgb(44, 111, 111);
    color: rgb(240, 235, 235);
}
</style>