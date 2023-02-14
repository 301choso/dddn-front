<script setup lang="ts">
import {ref} from "vue";
import {useRouter} from "vue-router";
import axios from "axios";

const router = useRouter();

const props = defineProps({
    boardId: {
        type: [Number, String],
        require: true,
    },
});

const board = ref({
    boardId: 0,
    boardTitle: "",
    boardContent: "",
});

axios.get(`/dddn/api/board/${props.boardId}`).then((response) => {       
    board.value = response.data;
});

const edit = () => {
    axios.patch(`/dddn/api/board/${board.boardId}`, board.value).then(() => {       
    router.replace({name: "home"});
    });
}
</script>

<template>
    <div>
        <el-input v-model="board.boardTitle" />
    </div>

    <div class="mt-2">
        <el-input v-model="board.boardContent" type="textarea" rows="15"/>
    </div>

    <div class="mt-2">
        <el-button type="warning" @click="edit()">수정완료</el-button>
    </div>
</template>

<style>

</style>