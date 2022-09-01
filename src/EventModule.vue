<script>
    import FriendModule from './FriendModule.vue'
    export default {
    created() {
        console.log('created')
    },
    data() {
        return {
            eventsList: this.eventsProps
        }
    },
    emits: ['remove'],
    methods: {
        removeEvent(selectedEvent) {
            this.eventsList = this.eventsList.filter((l) => { return l !== selectedEvent })
            this.$emit('remove', this.eventsList)
        }
    },
    props: {
        'eventsProps': Object
    },
    components: { 
        FriendModule 
    },
    mounted() {
        console.log("mounted")
    },
    updated() {
        console.log("changed")
    },
    unmounted() {
        console.log("unmounted")
    }
}
</script>

<template>
    <div class="m-4 mx-[10%] p-8 border-dotted border-2 border-indigo-800 rounded" v-for="event in eventsList">
        <div class="mb-4">
            <p class="text-2xl"><span class="px-2 py-1 border-solid border-2 border-indigo-800 bg-indigo-500 text-white rounded">Event</span> - {{ event.eventTitle }}</p>
            <p class="text-xs text-right">{{ event.description }}</p>
            <p class="text-xs text-right">Date: {{ event.date }}</p>
        </div>
        <FriendModule :friendsProps="event.friendsList" />
        <button class="border-solid border-2 border-red-600 bg-red-500 text-white rounded" @click="removeEvent(event)" >Remove</button>
    </div>
</template>