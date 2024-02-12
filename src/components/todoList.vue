<script setup>
    import { ref } from 'vue'
    let id = 0
    const todo = ref("")
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
    function addTD(){
        if (todo.value !== "")
            todoList.value.push({id:id++, text: todo.value})
        todo.value = ""
    }
    function deleteTD(id){
        todoList.value = todoList.value.filter((obj) => obj.id !== id)
    }
</script>
<template>
    <v-container class="d-flex justify-center">
        <v-card width="600">
            <v-text-field 
                label="Add To Do" 
                v-model="todo"
                @keydown.enter="addTD"
                append-inner-icon="mdi-plus"
            ></v-text-field>

            <v-list class="ml-6">
                <v-list-item 
                    v-for="todo in todoList"
                    :key="todo.id"
                >
                    {{ todo.text }}
                    <template v-slot:append >
                        <v-btn 
                            icon="mdi-trash-can-outline" 
                            size="small"
                            variant="text"
                            @click="deleteTD(todo.id)"
                        ></v-btn>
                    </template>
                </v-list-item>
            </v-list>
            
        </v-card>
        
    </v-container>
    
</template>