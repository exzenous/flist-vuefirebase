<script>
    
</script>

<template>
    <div class="backdrop">
        <div class="modal">
            <h2 class="text-3xl text-center">Event name</h2>
            <div class="text-center">
                <label for="description">Description</label><input class="border" type="text"><br>
                <label for="date">Date</label><input class="border" type="text"><br>
                <label for="something1">Something</label><input class="border" type="text"><br>
                <button class="ml-6 min-w-[15%] border-solid border-2 border-indigo-800 bg-indigo-500 text-white rounded">Add</button>
            </div>
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