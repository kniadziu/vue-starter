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
                       :username="user"
                       @register="addParticipantToMeeting($event)"
                       @unregister="deleteParticipantFromMeeting($event)"
                       @delete="deleteMeeting($event)"
        >
        </meetings-list>
    </div>
</template>

<script>
    import NewMeetingForm from "./NewMeetingForm";
    import MeetingsList from "./MeetingsList";

    export default {
        components: {NewMeetingForm, MeetingsList},
        props: ['user'],
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
                meeting.participants.push(this.user)
            },

            deleteParticipantFromMeeting(meeting) {
                meeting.participants.splice(meeting.participants.indexOf(this.user), 1);
            },
            deleteMeeting(meeeting) {
                this.meetings.splice(this.meetings.indexOf(meeting),1);
            }


        }
    }
</script>
