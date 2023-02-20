<script lang="ts" setup>
import { ref } from 'vue'

const form = ref({
    memberNum: 0,
    memberId: "",
    memberPw: "",
});

const onSubmit = () => {
  console.log('submit!')
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