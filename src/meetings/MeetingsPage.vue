<template>
    <div>
       <!--<h2>System do zapisow na zajecia</h2> -->
        <new-meeting-form @added="addNewMeeting($event)"></new-meeting-form>
        <span v-if="meetings.length == 0">
               Brak spotkań.
           </span>
        <h3 v-else>
            Zaplanowane zajęcia ({{ meetings.length }})
        </h3>
        <meetings-list :meetings="meetings"></meetings-list>
    </div>
</template>

<script>
    import NewMeetingForm from "./NewMeetingForm";
    import MeetingsList from "./MeetingsList";

    export default {
        components: {NewMeetingForm, MeetingsList},
        data() {
            return {
                meetings: []
            };
        },
        methods: {
            addNewMeeting(meeting) {
                this.meetings.push(meeting);
            }
        }
    }
</script>
