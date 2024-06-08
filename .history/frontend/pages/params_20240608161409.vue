<script setup>

const numOfFewShots = ref(null)
const numOfGenSamples = ref(null)


</script>


<template>
    <div class="flex h-full min-h-screen">
        <!-- 左侧目录栏 -->
        <div class="p-4 flex flex-col w-1/6 bg-gray-200">
            <div class="space-y-4 flex-grow">
                <NuxtLink to="/api" class="p-4 bg-gray-400 rounded-xl flex items-center justify-center cursor-pointer">API</NuxtLink>
                <NuxtLink to="/prompt" class="p-4 bg-gray-400 rounded-xl flex items-center justify-center cursor-pointer">Prompt</NuxtLink>
                <NuxtLink to="/params" class="p-4 bg-gray-500 rounded-xl flex items-center justify-center cursor-pointer">Params</NuxtLink>
            </div>
        </div>
        
        <!-- 右侧内容区域 -->
        <div class="p-10 w-5/6 bg-white">
            <div class="">
                <label>Number of few-shots</label>
                <select v-model="numOfFewShots" class="mt-2 mb-4 border w-full rounded-xl p-2">
                    <option>1</option>
                </select>

            </div>
        </div>

    </div>
</template>