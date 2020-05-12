<template>
    <div>
        <form @submit.prevent="addNewMeeting()" v-if="adding">

                <h3>Dodaj nowe spotkanie</h3>
            <div  class="nazwa">
                <label>Nazwa</label>
                <input type="text" v-model="newMeeting.name">
            </div>

            <div class="data">
                <label>Planowana data</label>
                <datetime v-model="newMeeting.datetime" type="datetime" ></datetime>
            </div>

            <div  >
                <label>Opis</label>
                <textarea v-model="newMeeting.description"></textarea>
            </div>


    <button>Dodaj</button>
    <span class="error" v-if="error">Spotkanie musi mieć nazwę!</span>


        </form>
        <button @click="adding = true" v-else>Dodaj nowe spotkanie</button>
    </div>
</template>


<script>
    import { Datetime } from 'vue-datetime';

    export default {
        components: {datetime: Datetime},

        data() {
            return {
                newMeeting: { participants: [] },
                adding: false,
                error: false,
                datetime: null,
            };
        },
        methods: {
            addNewMeeting() {
                this.error = false;
                if (this.newMeeting.name) {
                    this.$emit('added', this.newMeeting);
                    this.newMeeting = { participants: [] };
                    this.adding = false;
                } else {
                    this.error = true;
                }
            }
        }
    }
</script>


<style scoped>
    .error {
        color: #1d65d2;
    }

    .nazwa {
        float:left;
        width:79%;

    }

    .data {
        float:right;
        width:20%;

    }

</style>