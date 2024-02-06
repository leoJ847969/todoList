<script setup>
    import { ref } from 'vue'
    let id = 0
    const listTitleText = ref("")
    const listTitles = ref([
        {
            id: id++,
            text:"Day1"
        },
        {
            id: id++,
            text:"Day2"
        },
        {
            id: id++,
            text:"Day3"
        },
    ])
    function addTDList(){
        if(listTitleText.value != "")
            listTitles.value.push({text: listTitleText.value})
        listTitleText.value = ""
    }
    
</script>
<template>
    <v-navigation-drawer permanent=true>
        <v-text-field  v-model="listTitleText" >
            <template v-slot:append-inner>
                <v-btn block @click="addTDList" > + </v-btn>
            </template>    
        </v-text-field>
        
            
        <v-list>   
            <v-list-item v-for="(item, i) in listTitles" :key="i" :value="item">
                {{ item.text }}
            </v-list-item>
        </v-list>
    </v-navigation-drawer>
</template>






