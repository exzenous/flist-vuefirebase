<script>

    export default {
        created() {
        },
        data() {
            return {
                newFriendName: "",
                friendsList: this.friendsProps
            }
        },
        props: {
            'friendsProps': Array
        },
        methods: {
            addFriend(name) {
                if (name != "") {
                    this.friendsList.push({
                        name: name,
                        facebookUrl: "www.fb.com/aaa",
                        addedStatus: false
                    })
                    this.newFriendName = ""
                }
            },
            removeFriend(friend) {
                this.friendsList = this.friendsList.filter((t) => { return t !== friend})
            }
        }
    }
</script>

<template>
    <div class="p-2 rounded bg-slate-100 flex w-full mb-4" >
        <input v-model="newFriendName" class="flex-grow rounded p-2" type="text" placeholder="Add Friend...">
        <button class="ml-6 min-w-[15%] border-solid border-2 border-indigo-800 bg-indigo-500 text-white rounded" @click="addFriend(newFriendName)">Add Friend</button>
    </div>
    <ul>
        <li class="flex" v-for="friend in friendsList">
            <div class="w-8 h-8 bg-cyan-300"></div>
            <p class="flex-grow" >{{ friend.name }}</p>
            <p><a class="min-w-6" :href="'http://' + friend.facebookUrl">Facebook</a></p>
            <button class="border-solid border-2 border-red-600 bg-red-500 text-white rounded" @click="removeFriend(friend)">Delete</button>
        </li>
    </ul>
</template>