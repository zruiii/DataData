<script setup>

import { ref } from 'vue'

const customHeight = ref('300px')
const customWeight = ref('200px')

const prompts = ref([
  { id: 1, name: '多中心找点', task: 'Task 1', description: 'Description 1'},
  { id: 2, name: '实时交通', task: 'Task 2', description: 'Description 2'}
])

const showMode = ref(false)
const editMode = ref(false)
const newPromptName = ref('')
const newPrompDesc = ref('')




</script>

<template>
    <div class="flex h-full min-h-screen">
        <!-- 左侧目录栏 -->
        <div class="p-4 flex flex-col w-1/6 bg-gray-200">
            <div class="space-y-4 flex-grow">
                <NuxtLink to="/api" class="p-4 bg-gray-400 rounded-xl flex items-center justify-center cursor-pointer">API</NuxtLink>
                <NuxtLink to="/prompt" class="p-4 bg-gray-500 rounded-xl flex items-center justify-center cursor-pointer">Prompt</NuxtLink>
                <NuxtLink to="/params" class="p-4 bg-gray-400 rounded-xl flex items-center justify-center cursor-pointer">Params</NuxtLink>
            </div>
        </div>
        

        <!-- 右侧内容区域 -->
        <div class="p-10 w-5/6 bg-white">
            <div class="grid grid-cols-3 gap-20">
                <div
                    class="p-4 flex items-center justify-center rounded-xl bg-gray-200 cursor-pointer"
                    :style="{ height: customHeight }"
                    v-for="prompt in prompts"
                    :key="prompt.id"
                >
                    <p class="text-2xl"> {{ prompt.name }} </p>
                </div>

                <div class="flex items-center justify-center">
                    <button @click="" class="p-4 flex items-center justify-center rounded-full bg-gray-200 cursor-pointer" :style="{ height: customWeight, width: customWeight }">
                        <span class="text-4xl"> + </span>
                    </button>
                </div>
            </div>
        </div>

        <!-- 模态框 -->
        <div v-if="showMode">
            <div class="bg-white p-6 rounded-lg shadow-lg">

            </div>
        </div>

    </div>
</template>