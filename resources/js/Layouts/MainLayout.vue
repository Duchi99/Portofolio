<script setup>
import SideNav from '@/Components/SideNav.vue';
import { ref } from 'vue'

const isCollapsed = ref(true);
const toggleSidebar = () => {
    isCollapsed.value = !isCollapsed.value
}
</script>

<template>
    <div>
        <SideNav :isCollapsed="isCollapsed" @toggleSidebar="toggleSidebar"/>
    </div>
</template>