<script setup>

const numOfFewShots = ref(3)
const numOfGenSamples = ref(3)
const genInterval = ref(1)
const divLevel = ref(0)

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
        <div class="p-10 w-5/6 bg-white space-y-6">
            <div>
                <label>Number of few-shots</label>
                <select v-model="numOfFewShots" class="mt-2 mb-4 border w-full rounded-xl p-2">
                    <option>1</option>
                    <option>2</option>
                    <option>3</option>
                    <option>4</option>
                    <option>5</option>
                    <option>6</option>
                </select>
            </div>

            <div>
                <label>Number of new-samples</label>
                <select v-model="numOfGenSamples" class="mt-2 mb-4 border w-full rounded-xl p-2">
                    <option>1</option>
                    <option>2</option>
                    <option>3</option>
                    <option>4</option>
                </select>
                <small class="text-gray-600">合成间隔指定算法每次打印结果滚动轮次。建议设置为1来避免脏数据混入种子样本库。</small>
            </div>

            <div>
                <label>Gneration Interval</label>
                <select v-model="genInterval" class="mt-2 mb-4 border w-full rounded-xl p-2">
                    <option>1</option>
                    <option>2</option>
                    <option>3</option>
                </select>
                <small class="text-gray-600">合成间隔指定算法每次打印结果滚动轮次。建议设置为1来避免脏数据混入种子样本库。</small>
            </div>

            <div>
                <label>Diversity Level</label>
                <select v-model="divLevel" class="mt-2 mb-4 border w-full rounded-xl p-2">
                    <option>0</option>
                    <option>1</option>
                    <option>2</option>
                    <option>3</option>
                    <option>4</option>
                    <option>5</option>
                </select>
                <small class="text-gray-600">丰富度等级越高，系统会自动过滤掉和已有样本相似度较大的生成样本。丰富度等级设置为0时，系统不对生成样本进行自动过滤。</small>
            </div>
        </div>

    </div>
</template>