<template>
    <div>
        <label>Zaloguj się e-mailem</label>
        <input type="email" v-model="userLogin">
        <button @click="enter()">{{ buttonLabelToDisplay }}</button>
    </div>
</template>

<script>
    export default {
        props: ['buttonLabel'],
        data() {
            return {
                userLogin: ''
            }
        },
        methods: {
            enter() {
                this.$emit("login", this.userLogin);

            }
        },
        computed: {
            buttonLabelToDisplay() {
                return this.buttonLabel || 'Zaloguj się';
            }

        }
    }
</script>
