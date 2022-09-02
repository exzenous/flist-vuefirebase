<script>
    import EventModule from './EventModule.vue'
    import ModalAddEvent from './components/ModalAddEvent.vue'

    export default {
        data() {
            return {
                isAddingEvent: false,
                newEventTitle: "",
                localStorage: [
                    // {
                    //     eventTitle: "CosNatsu #3", 
                    //     description: "A Bi-yearly Cosplay Event", 
                    //     date: "10/08/2022", 
                    //     friendsList: [
                    //         {
                    //             name: "Kiitsak Jamkhom",
                    //             facebookUrl: "www.fb.com/aaa",
                    //             addedStatus: false
                    //         },
                    //         {
                    //             name: "Kiitsak Jamkhom",
                    //             facebookUrl: "www.fb.com/aaa",
                    //             addedStatus: false
                    //         }
                    //     ]
                    // }
                ]
            }
        },
        methods: {
            toggleModal() {
              this.isAddingEvent = !this.isAddingEvent
            },
            addEvent(newTitle) {
                this.toggleModal()
                this.localStorage.push(newTitle)
                this.newEventTitle = ""
            },
            updateList(newList) {
                this.localStorage = newList
            }
        },
        components: {
            EventModule,
            ModalAddEvent
        }
    }
</script>

<template>
    <ModalAddEvent v-if="isAddingEvent" :eventProps="newEventTitle" @close="toggleModal" @updateList="addEvent"/>
    <div class="m-4 p-4 rounded bg-slate-200">
        <h1 class="p-4 text-3xl text-center">'Flist' - Friends List Management</h1>
        <div class="flex w-full">
            <input v-model="newEventTitle" class="flex-grow rounded p-2" type="text" placeholder="Event Name...">
            <button class="ml-6 min-w-[15%] border-solid border-2 border-indigo-800 bg-indigo-500 text-white rounded" @click="toggleModal">Add</button>
        </div>
    </div>
    <!-- TODO: LET'S MAKE A POPUP MODAL FOR ADDITIONAL INFOS-->
    <EventModule :eventsProps="localStorage" @remove="updateList"/>
</template>
