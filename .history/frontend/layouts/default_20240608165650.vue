<template>
    <div class="flex flex-col min-h-screen">
        <nav class="px-10 py-4 flex items-center justify-between bg-blue-300">
            <NuxtLink to="/" class="text-xl">DataData</NuxtLink>

            <div class="flex items-center space-x-4">
                <NuxtLink to="/" class="text-xl">Data</NuxtLink>
                <NuxtLink to="/api" class="text-xl">Setting</NuxtLink>
            </div>
        </nav>

        <div class="flex-grow">
            <slot/>
        </div>
        
        
        <footer class="p-4 flex flex-wrap items-center justify-between bg-blue-200">
            <p>Copyright (c) 2024 - DataData</p>
        </footer>
    </div>
</template>
