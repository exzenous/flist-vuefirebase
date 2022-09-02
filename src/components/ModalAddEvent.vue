<script>
    export default {
        emits: ['close', 'updateList'],
        data() {
            return {
                newEventEntity: {
                    eventTitle: this.eventProps,
                    description: "",
                    date: "",
                    friendsList: []
                }
            }
        },
        props: {
            'eventProps': String
        },
        methods: {
            updateList() {
                this.$emit('updateList', this.newEventEntity)
            },
            closeModal() {
                this.$emit('close')
            }
        }
    }
</script>

<template>
    <div class="backdrop">
        <div class="modal">
            <h2 class="text-3xl text-center">Adding: {{ eventProps }}</h2>
            <div class="p-8 text-center">
                <label for="description">Description</label><input v-model="newEventEntity.description" class="border" type="text"><br>
                <label for="date">Date</label><input v-model="newEventEntity.date" class="border" type="text"><br>
                <button class="my-4 ml-6 min-w-[15%] border-solid border-2 border-indigo-800 bg-indigo-500 text-white rounded" @click="this.updateList()">Add</button>
                <button class="my-4 ml-6 min-w-[15%] border-solid border-2 border-indigo-800 bg-indigo-500 text-white rounded" @click="closeModal">Close</button>
            </div>
            <p>{{ newEventEntity }}</p>
        </div>
    </div>
</template>

<style scoped>
.backdrop {
    top: 0;
    position: fixed;
    background: rgba(0, 0, 0, 0.5);
    width: 100%;
    height: 100%;
}
.modal {
    width: 80%;
    padding: 20px;
    margin: 100px auto;
    background: white;
    border-radius: 10px;
}
</style>