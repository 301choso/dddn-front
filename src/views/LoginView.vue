<script lang="ts" setup>
import axios from 'axios';
import { ref } from 'vue'
import {useRouter} from "vue-router";

const router = useRouter();

const form = ref({
    memberNum: 0,
    memberId: "",
    memberPw: "",
});

const onSubmit = () => {
  axios.post("/dddn/api/auth/login", form.value).then(() => {       
    router.replace({name: "home"});
  });
}
</script>

<template>
로그인
  <el-form :model="form" label-width="120px">
    <el-form-item label="ID">
      <el-input v-model="form.memberId" />
    </el-form-item>

    <el-form-item label="PW">
      <el-input v-model="form.memberPw" />
    </el-form-item>

    <el-form-item>
      <el-button>Join</el-button>
      <el-button type="primary" @click="onSubmit">Login</el-button>
    </el-form-item>
    비밀번호를 잊으셨나요?
  </el-form>
</template>