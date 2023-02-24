<script setup lang="ts">
import {defineProps, onMounted, ref} from "vue";
import {useRouter} from "vue-router";
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

const router = useRouter();

const moveToEdit = () => {
    router.push({name: "edit"})
}

onMounted(() => {
    axios.get(`/dddn/api/board/${props.boardId}`).then((response) => {       
        board.value = response.data;
    });

});
</script>

<template>
    <el-row>
        <el-col>
            <h2 class="title">
                <p v-html="board.boardTitle"></p>
            </h2>

            <div class="sub d-flex">
                <div class="category">{{board.boardCategory}}</div>
                <div class="regDt">{{board.boardDate}}</div>
            </div>
        </el-col>
    </el-row>
    
    <el-row>
        <el-col>
            <div class="content">
                <p v-html="board.boardContent"></p>
            </div>
        </el-col>
    </el-row>

    <el-row>
        <el-col>
            <div class="d-flex justify-content-end">
            <el-button type="warning" @click="moveToEdit()">수정</el-button>
            </div>
        </el-col>
    </el-row>
</template>

<style scoped lang="scss">
    .title {
        font-size: 1.6rem;
        font-weight: 600;
        color: #383838;
        margin: 0;
    }

    .content {
      font-size: 0.95rem;
      margin-top: 12px;
      color: #7e7e7e;
      white-space: break-spaces;
      line-height: 1.5;
      
    }

    .sub {
      margin-top: 6px;
      font-size: 0.78rem;
      
      .regDt {
        margin-left: 10px;
        color: #6b6b6b;
      }
    }
</style>