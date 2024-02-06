<script setup>
    import { ref } from 'vue'
    let id = 0
    const todoList = ref([
        {
            id: id++,
            text: "Do the dishes"
        },
        {
            id: id++,
            text: "Take out the garbage"
        },
        {
            id: id++,
            text: "Buy some food"
        },

    ]) 
</script>
<template>
    <v-container class="d-flex justify-center">
        <v-card width="600">
            <v-list class="ml-5">
                <v-list-item v-for="todo in todoList" :key="todo.id">
                    {{ todo.text }}
                    <template v-slot:append >
                        <v-btn icon="mdi-trash-can-outline" size="small" variant="text"></v-btn>
                    </template>
                </v-list-item>
            </v-list>
        </v-card>
    </v-container>
    
</template>