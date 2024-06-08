<script setup>

import { ref } from 'vue'

const customHeight = ref('300px')
const customWeight = ref('200px')

const prompts = ref([
  { id: 1, name: '多中心找点', task: 'Task 1', description: 'Description 1'},
  { id: 2, name: '实时交通', task: 'Task 2', description: 'Description 2'}
])

const showMode = ref(true)
const editMode = ref(false)
const newPromptName = ref('')
const newPromptTask = ref('')
const newPromptDesc = ref('')
const selectedPromptIndex = ref(null)

const initPrompt = () => {
    showMode.value = true
    editMode.value = false
    newApiName.value = ''
    newApiCategory.value = ''
    newApiToken.value = ''
    selectedApiIndex.value = null
}


const addPrompt = () => {
    if (newPromptName.value.trim() !== '') {
        prompts.value.push({
            id: prompts.value.length + 1,
            name: newPromptName.value,
            task: newPromptTask.value,
            description: newPromptDesc.value
        })
    }
    newPromptName.value = ''
    newPromptTask.value = ''
    newPromptDesc.value = ''
    selectedPromptIndex.value = null
    showMode = false
    editMode = false
}


const editPrompt = (index) => {
    const prompt = prompts.value[index]
    newPromptName.value = prompt.name
    newPromptTask.value = prompt.task
    newPromptDesc.value = prompt.description
    editMode = true
    showMode = true
    selectedPromptIndex.value = index
}



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
                    v-for="(prompt, index) in prompts"
                    :key="prompt.id"
                    @click="editPrompt(index)"
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
        <div v-if="showMode" class="fixed inset-0 flex items-center justify-center bg-gray-800 bg-opacity-50">
            <div class="bg-white p-6 rounded-lg shadow-lg">
                <h2 class="text-xl mb-4">{{ editMode ? 'Edit Prompt' : 'Add New Prompt' }}</h2>
                <div>
                    <label>Name</label>
                    <input v-model="newPromptName" type="text" class="mt-2 mb-4 border w-full rounded-xl p-2">
                </div>

                <div>
                    <label>Task</label>
                    <input v-model="newPromptTask" type="text" class="mt-2 mb-4 border w-full rounded-xl p-2">
                </div>

                <div>
                    <label>Description</label>
                    <textarea v-model="newPromptDesc" type="text" class="mt-2 mb-4 border w-full rounded-xl p-2"></textarea>
                </div>

                <div class="flex justify-end space-x-4 mt-4">
                    <button @click="showMode = false" class="bg-gray-500 text-white px-4 py-2 rounded">Cancel</button>
                    <button v-if="!editMode" @click="addPrompt" class="bg-blue-500 text-white px-4 py-2 rounded">Add</button>
                    <button v-if="editMode" @click="savePrompt" class="bg-blue-500 text-white px-4 py-2 rounded">Save</button>
                    <button v-if="editMode" @click="removePrompt" class="bg-blue-500 text-white px-4 py-2 rounded">Remove</button>
                </div>

            </div>
        </div>

    </div>
</template>