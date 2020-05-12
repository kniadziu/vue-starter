<template>
    <table v-if="meetings.length > 0">
        <thead>
        <tr>
            <th width="1%">Lp.</th>
            <th width="15%">Nazwa spotkania</th>
            <th width="25%">Opis</th>
            <th width="15%">Data</th>
            <th width="15%">Uczestnicy</th>
            <th></th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="(meeting, n) in meetings" :key="meeting.name">
            <td>{{ n+1 }}</td>
            <td>{{ meeting.name }}</td>
            <td>{{ meeting.description }}</td>
            <td>{{ formatDate(meeting.datetime)}}</td>
            <!-- <td><span>{{ meeting.datetime | moment("dddd, MMMM Do YYYY") }}</span></td>-->
            <td>
                <ul v-if="meeting.participants">
                    <li v-for="user in meeting.participants" :key="user">
                        {{ user }}
                    </li>
                </ul>
            </td>
            <td>
                <button v-if="meeting.participants.indexOf(username) <0" class="button-outline"
                        @click="$emit('register', meeting)">Zapisz się
                </button>

                <button v-else class="button-outline" @click="$emit('unregister', meeting)">Wypisz się</button>
                &nbsp
                <button v-if="meeting.participants.length === 0" class="button" @click="$emit('delete', meeting)">
                    Usuń puste spotkanie
                </button>

            </td>

        </tr>
        </tbody>
    </table>
</template>

<script>
    import moment from 'moment';

    export default {
        components: {moment},
        props: ['meetings', 'username'],
        methods: {
            formatDate: function (dt) {
                //   return moment(dt).format("dddd, MMMM Do YYYY, h:mm:ss a");
                return moment(dt).format("YYYY-MM-DD HH:mm");
            }
        }

    }
</script>


<style scoped>


</style>