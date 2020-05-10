<template>
    <table v-if="meetings.length > 0">
        <thead>
        <tr>
            <th width ="20%">Nazwa spotkania</th>
            <th width ="30%">Opis</th>
            <th width ="20%">Uczestnicy</th>
            <td ></td>
        </tr>
        </thead>
        <tbody>
        <tr v-for="meeting in meetings" :key="meeting.name">
            <td >{{ meeting.name }}</td>
            <td>{{ meeting.description }}</td>
            <td>
                <ul v-if="meeting.participants">
                    <li v-for="user in meeting.participants" :key="user">
                        {{ user }}
                    </li>
                </ul>
            </td>
            <td>
                <button v-if="meeting.participants.indexOf(username) < 0" class="button-outline"
                        @click="this.$emit('register', meeting)" >Zapisz się
                </button>

                <button v-else class="button-outline" @click="this.$emit('unregister', meeting)">Wypisz się</button>

                <button v-if="meeting.participants.length === 0" class="button" @click="this.$emit('delete', meeting)">
                    Usuń puste spotkanie
                </button>

            </td>

        </tr>
        </tbody>
    </table>
</template>

<script>
    export default {
        props: ['meetings', 'username'],



    }
</script>
