<script setup lang="ts">
import { useChatStore } from "@/stores/chat";
const chatStore = useChatStore();
import { useRouter } from "vue-router";
const router = useRouter();
import HotWords from "./HotWords.vue";
import Input from "./Input.vue";

const sendQuestion = (question: string) => {
  console.log(555);
  router.push({
    path: "/chat",
  });
  //   chatStore.setQuestion(question)
  //   chatStore.setMode(mode.value)
  //   chatStore.setShowResult(true)
};
</script>
<template>
  <div class="mx-auto w-11/12 md:w-1/2">
    <div
      class="bg-[url(/src/assets/image/introduction/bg_introduction.png)] bg-cover bg-center rounded-xl bg-no-repeat w-full h-[330px] mx-auto mt-24 overflow-hidden"
    >
      <div
        class="bg-gradient-to-r from-[#1e3b8ae0] to-[#0285c7e0] w-full h-full text-white flex flex-col justify-between p-6"
      >
        <h2 class="text-xl font-normal tracking-wide">
          Hi,我是您的民用航空器维修智能助手，我可以回答任何民用航空器维修相关的问题。
        </h2>
        <ul class="text-sm ml-4">
          <li class="list-disc py-4">有关民用航空器维修的介绍有哪些？</li>
          <li class="list-disc py-4">民用航空器维修的种类是哪些？</li>
          <li class="list-disc py-4">如何针对民用航空器维修流程进行优化？</li>
        </ul>
        <div class="pt-4 text-xs">
          <button class="px-3 py-2 rounded-xl mr-4 border border-white">
            民用航空器维修查询
          </button>
          <button class="px-3 py-2 rounded-xl mr-4 border border-white">
            民用航空器维修智能分析
          </button>
          <button class="px-3 py-2 rounded-xl mr-4 border border-white">
            常用维修报告撰写
          </button>
        </div>
      </div>
    </div>
    <HotWords class="mt-1" />
  </div>
  <!-- <Input @sendQuestion = "sendQuestion"/> -->
</template>
