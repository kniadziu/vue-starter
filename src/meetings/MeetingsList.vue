<template>
    <table v-if="meetings.length > 0">
        <thead>
        <tr>
            <th width ="20%">Nazwa spotkania</th>
            <th width ="30%">Opis</th>
            <th width ="20%">Uczestnicy</th>
            <th ></th>


        </tr>
        </thead>
        <tbody>
        <tr v-for="meeting in meetings" :key="meeting.name">
            <td width ="20%">{{ meeting.name }}</td>
            <td>{{ meeting.description }}</td>
            <td>{{ meeting.description }}</td>
            <td>
                <button @click="registering = false" :class="registering ? 'class=float-right button-outline' : ''">Zapisz się</button>
                <button @click="registering = true" :class="!registering ? 'class=float-right button-outline' : ''">Wypisz się</button>

            </td>

        </tr>
        </tbody>
    </table>
</template>

<script>
    export default {

        props: ['meetings', 'email'],
        data(){
            return {
                registering: false
            }
        }
    }
</script>
