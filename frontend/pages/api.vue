<script setup>
import { ref } from 'vue'

const customHeight = ref('300px')
const customWeight = ref('200px')

const showMode = ref(false)
const editMode = ref(false)
const newApiName = ref('')
const newApiCategory = ref('')
const newApiToken = ref('')


const apis = ref([
  { id: 1, name: 'EB4.0', category: 'Category 1', token: 'token1' },
  { id: 2, name: 'DeepSeek', category: 'Category 2', token: 'token2' }
])

const categories = ref([
{ id: 1, name: 'Category 1' },
{ id: 2, name: 'Category 2' },
{ id: 3, name: 'Category 3' },
])

const editApi = (index) => {
    const api = apis.value[index]
    newApiName.value = api.name
    newApiCategory.value = api.category
    newApiToken.value = api.token
    showMode.value = true
    editMode.value = true
    // console.log(newApiName)
}


const addApi = () => {
  if (newApiName.value.trim() !== '') {
    apis.value.push({
        id: apis.value.length + 1,
        name: newApiName.value,
        category: newApiCategory.value,
        token: newApiToken.value
    })
    newApiName.value = ''
    showMode.value = false
  }
}


const removeApi = (index) => {
    const api = apis.value[index]
}

</script>


<template>
    <div class="flex h-full min-h-screen">
        <!-- 左侧目录栏 -->
        <div class="p-4 flex flex-col w-1/6 bg-gray-200">
            <div class="space-y-4 flex-grow">
                <NuxtLink to="/api" class="p-4 bg-gray-500 rounded-xl flex items-center justify-center cursor-pointer">API</NuxtLink>
                <NuxtLink to="/prompt" class="p-4 bg-gray-400 rounded-xl flex items-center justify-center cursor-pointer">Prompt</NuxtLink>
                <NuxtLink to="/params" class="p-4 bg-gray-400 rounded-xl flex items-center justify-center cursor-pointer">Params</NuxtLink>
            </div>
        </div>
  
        <!-- 右侧内容区域 -->
        <div class="w-5/6 bg-white p-4">
            <div class="grid grid-cols-3 gap-20">
                <div
                    v-for="(api, index) in apis"
                    :key="api.id"
                    class="p-4 flex items-center justify-center rounded-xl bg-gray-200 cursor-pointer"
                    :style="{ height: customHeight }"
                    @click="editApi(index)"
                >
                    <p class="text-xl"> {{ api.name }} </p>
                </div>

                <div class="flex items-center justify-center">
                    <button @click="showMode = true" class="p-4 flex items-center justify-center rounded-full bg-gray-200 cursor-pointer" :style="{ height: customWeight, width: customWeight }">
                        <span class="text-4xl"> + </span>
                    </button>
                </div>
            </div>
        </div>

        <!-- 模态框 -->
        <div v-if="showMode" class="fixed inset-0 flex items-center justify-center bg-gray-800 bg-opacity-50">
            <div class="bg-white p-6 rounded-lg shadow-lg">
                <h2 class="text-xl mb-4">{{ editMode.value ? 'Edit API' : 'Add New API' }}</h2>
                <div>
                    <label>Name</label>
                    <input v-model="newApiName" type="text" class="mt-2 mb-4 border w-full rounded-xl p-2">
                </div>

                <div>
                    <label>Category</label>
                    <select v-model="newApiCategory" class="mt-2 mb-4 border w-full rounded-xl p-2">
                        <option value="">{{ editMode.value ? 'Select Category' : 'Select Category' }}</option>
                        <option 
                            v-for="category in categories" 
                            v-bind:key="category.id" 
                            v-bind:value="category.id"
                        >
                            {{ category.name }}
                        </option>
                    </select>                    
                </div>


                <div>
                    <label>Token</label>
                    <input v-model="newApiToken" type="text" class="mt-2 mb-4 border w-full rounded-xl p-2">
                </div>


                <div class="flex justify-end space-x-4 mt-4">
                    <button @click="showMode = false" class="bg-gray-500 text-white px-4 py-2 rounded">Cancel</button>
                    <button v-if="editMode = false" @click="addApi" class="bg-blue-500 text-white px-4 py-2 rounded">Add</button>
                    <button @click="removeApi" class="bg-blue-500 text-white px-4 py-2 rounded">Remove</button>
                </div>
            </div>
        </div>
    </div>
</template>