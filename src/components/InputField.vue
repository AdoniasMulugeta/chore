<template>
    <div>
        <label for="todo-field"></label>
        <input id="todo-field" :placeholder="placeholder" v-model="newInput" @keyup.enter="input">
    </div>
</template>

<script>
    export default {
        name: "InputField",
        props: {
            placeholder: { type: String, default: 'Input Here ...' },
        },
        data: () => ({
            newInput: '',
        }),
        methods: {
            input() {
                this.$emit('input', this.newInput)
            }
        }
    }
</script>

<style scoped>

</style>
