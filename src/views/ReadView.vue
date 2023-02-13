<script setup lang="ts">
import {defineProps, onMounted, ref} from "vue";
import axios from "axios";

const props = defineProps({
    boardId: {
        type: [Number, String],
        require: true,
    },
});

const board = ref({
    id: 0,
    title: "",
    content: "",
});

onMounted(() => {
    axios.get(`/dddn/api/board/${props.boardId}`).then((response) => {       
        board.value = response.data;
    });

});
</script>

<template>
    <h2>{{board.boardTitle}}</h2>
    <div>{{board.boardContent}}</div>
</template>