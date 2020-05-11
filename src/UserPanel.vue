<template>
    <div >
        <h2>Witaj {{ username }}
        <button @click="logMeOut()" class="float-right  button-outline button">Wyloguj</button>
        </h2> </div>
</template>

<script>

    export default {

        props: ['username'],

        methods: {
            logMeOut() {
                this.$emit('logout');
            }
        }
    }
</script>
