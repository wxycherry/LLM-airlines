<script setup lang="ts">
import { ref } from "vue";
import { useRouter } from "vue-router";
const router = useRouter()
import History from "@/components/History.vue";
import { useUserStore } from "@/stores/user";
const userStore = useUserStore();
import { useChatStore } from "@/stores/chat";
import { postLogout } from "@/services/user";
const chatStore = useChatStore();
const isHistoryOpen = ref(false);
const logout = async () => {
  const result = await postLogout(userStore.user.account)
  if (result.code === 200) {
    userStore.logout()
    router.push("/login")
  }
}
</script>

<template>
  <header
    class="h-[60px] relative flex flex-wrap items-center justify-between text-center bg-[url('../src/assets/header.jpg')]"
  >
    <!-- <img src="../../assets/image/title.png" alt="" class="mx-auto h-[30px]" /> -->
    <p class="mx-auto h-[30px] title">民用航空器维修私域大模型</p>
    <!-- <button
      class="md:hidden block absolute top-5 left-4"
      @click="isHistoryOpen = true"
    >
      <img src="../../assets/history.png" width="29" />
    </button>
    <button
      class="md:hidden block absolute top-4 right-2"
      @click="chatStore.newQuestion"
    >
      <img src="../../assets/newChat.png" width="35" class="" />
    </button> -->
    <el-dropdown>
      <el-link :underline="false" class="mr-6 bg-white rounded-full"><img src="../../assets/user.png" width="36" alt=""></el-link>
      <template #dropdown>
        <el-dropdown-menu>
          <el-dropdown-item>编辑信息</el-dropdown-item>
          <el-dropdown-item divided @click="logout">退出登录</el-dropdown-item>
        </el-dropdown-menu>
      </template>
    </el-dropdown>
  </header>
  <History v-model="isHistoryOpen" />
</template>
<style scoped>
.title{
  font-size: 25px;
  color: white;
  font-weight: bold;
  font-family: KaiTi;

}
</style>
