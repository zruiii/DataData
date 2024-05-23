<script setup>
import { ref } from 'vue'

const categories = ref([
{ id: 1, name: 'Table-1' },
{ id: 2, name: 'Table-2' },
{ id: 3, name: 'Table-3' }
])

const items = ref([
{ id: 1, name: 'Sample 1' },
{ id: 2, name: 'Sample 2' },
{ id: 3, name: 'Sample 3' },
])

</script>


<template>
    <div class="flex h-full min-h-screen">
      <!-- 左侧目录栏 -->
      <div class="p-4 flex flex-col w-1/6 bg-gray-200">
        <ul class="space-y-4 flex-grow">
          <li v-for="category in categories" :key="category.id" class="p-4 bg-gray-400 rounded-xl">
            {{ category.name }}
          </li>
        </ul>
      </div>
  
      <!-- 右侧内容区域 -->
      <div class="w-5/6 bg-white p-4">
        <table class="min-w-full border-collapse">
          <thead>
            <tr>
              <th class="border-b-2 p-2 text-left w-1/6">ID</th>
              <th class="border-b-2 p-2 text-left w-5/6">Prompt</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item in items" :key="item.id" class="border-b">
                <td class="p-2 w-1/6">{{ item.id }}</td>
                <td class="p-2 w-5/6">{{ item.name }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
</template>
  
