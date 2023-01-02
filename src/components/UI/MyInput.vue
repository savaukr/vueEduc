<template>
    <input :value="modelValue" @input="updateInput" class='input' type="text">
</template>

<script>
export default {
    name: 'my-input',
    props: {
        modelValue: [String, Number]
    },
    methods: {
        updateInput(event) {
            this.$emit('update:modelValue', event.target.value)
        }
    }
}
</script>

<style scoped>
.input {
    width: 85%;
    padding: 8px 20px;
    border: 2px solid teal;
    margin-bottom: 15px;

}
</style>