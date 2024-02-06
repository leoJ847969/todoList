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
        <v-text-field density="compact" v-model="listTitleText" style="height: 40px;" ></v-text-field>
        <v-btn block @click="addTDList" rounded="0" variant="tonal"> + </v-btn>
        
        
        
        
        <v-list>   
            <v-list-item v-for="(item, i) in listTitles" :key="i" :value="item">
                {{ item.text }}
            </v-list-item>
        </v-list>
    </v-navigation-drawer>
</template>






