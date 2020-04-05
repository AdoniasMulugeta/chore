<template>
    <div>
        <label for="todo-field"></label>
        <input v-focus id="todo-field" :placeholder="placeholder" v-model="newInput" @keyup.enter="input">
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
                this.$emit('input', this.newInput);
                this.newInput = '';
            }
        },
        directives: {
            focus: {
                // directive definition
                inserted: function (el) {
                    el.focus()
                }
            }
        }

    }
</script>

<style scoped>
    #todo-field{
        margin-bottom: 10px;
    }
</style>
