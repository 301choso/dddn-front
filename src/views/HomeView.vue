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
      <div class="title">
        <router-link :to="{name: 'read', params: {boardId: board.boardId} }">
          <p v-html="board.boardTitle"></p>
        </router-link>
      </div>

      <div class="content">
        <p v-html="board.boardContent"></p>
      </div>

      <div class="sub d-flex">
        <div class="category">{{board.boardCategory}}</div>
        <div class="regDt">{{board.boardDate}}</div>
      </div>
    </li>
  </ul>
</template>

<style scoped lang="scss">
ul {
  list-style: none;
  padding: 0;

  li {
    margin-bottom: 1.8rem;

    .title {
      a {
        font-size: 1.1rem;
        color: #383838;
        text-decoration: none;
      }
      
      &:hover {
        background-color: #E5FFF8;
      }
    }

    .content {
      font-size: 0.85rem;
      margin-top: 8px;
      color: #7e7e7e;
    }

    &:last-child {
      margin-bottom: 0;
    }

    .sub {
      margin-top: 8px;
      font-size: 0.78rem;
      
      .regDt {
        margin-left: 10px;
        color: #6b6b6b;
      }
    }
  }
}
</style>
