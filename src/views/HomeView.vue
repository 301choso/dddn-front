<script setup lang="ts">
import axios from "axios";
import {ref} from "vue";
import {useRouter} from "vue-router";

const boards = ref([]);
const router = useRouter();

axios.get("/dddn/api/board").then((response) => {
  response.data.forEach((r: any) => {
    boards.value.push(r);
  });
});

</script>

<template>
  <ul>
    <li v-for="board in boards" :key="board.id">
      <div>
        <router-link :to="{name: 'read', params: {boardId: board.boardId} }">{{board.boardTitle}}</router-link>
      </div>

      <div>
        {{board.boardContent}}
      </div>
    </li>
  </ul>
</template>

<style scoped>
li {
  margin-bottom: 1rem;
}

li:last-child {
  margin-bottom: 0;
}
</style>
