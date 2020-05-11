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
        <meetings-list :meetings="meetings"
                       :username="username"
                       @register="addParticipantToMeeting($event)"
                       @unregister="deleteParticipantFromMeeting($event)"
                       @delete="deleteMeeting($event)">
        </meetings-list>
    </div>
</template>

<script>
    import NewMeetingForm from "./NewMeetingForm";
    import MeetingsList from "./MeetingsList";

    export default {
        components: {NewMeetingForm, MeetingsList},
        props: ['username'],
        data() {
            return {
                meetings: []
            };
        },
        methods: {
            addNewMeeting(meeting) {
                this.meetings.push(meeting);

            },

            addParticipantToMeeting(meeting) {
               // alert(this.username);
                meeting.participants.push(this.username);

            },

            deleteParticipantFromMeeting(meeting) {
                let indexToRemove = meeting.participants.indexOf(this.username);
                meeting.participants.splice(indexToRemove, 1);
            },

            deleteMeeting(meeting) {

                let indexToRemoveMeeting = this.meetings.indexOf(meeting);
                this.meetings.splice(indexToRemoveMeeting,1);
                ;
            }


        }
    }
</script>
