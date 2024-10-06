<script setup>
import { defineProps, defineEmits, ref, onMounted, onBeforeUnmount } from "vue";
import { Icon } from "@iconify/vue";
import { Link } from "@inertiajs/vue3";

const props = defineProps({
    isCollapsed: Boolean,
    default: false
});

const emit = defineEmits(["toggleSidebar"]);

const isMobile = ref(false); // Track mobile state

// Detect if viewport is in mobile mode
const handleResize = () => {
    isMobile.value = window.innerWidth < 640; // Tailwind's 'sm' breakpoint

    // Collapse sidebar on mobile
    if (isMobile.value) {
        emit("toggleSidebar", true);
    }
};

onMounted(() => {
    window.addEventListener("resize", handleResize);
    handleResize(); // Check on load
});

onBeforeUnmount(() => {
    window.removeEventListener("resize", handleResize);
});
</script>

<template>
    <nav
        :class="
            isCollapsed
                ? 'min-w-[5.5rem] max-w-[4.5rem]'
                : 'min-w-[12rem] max-w-[12rem]'
        "
        class="h-screen fixed top-0 left-0 bg-gradient-to-b from-gray-800 to-black transition-all duration-500 ease-in-out p-4"
    >
        <!-- Logo and Collapse Button -->
        <div
            :class="isCollapsed ? 'justify-center' : 'justify-between'"
            class="flex items-center mb-8"
        >
            <!-- Logo -->
            <Link
                v-if="!isCollapsed"
                :href="route('home')"
                class="text-2xl font-bold text-white tracking-wider"
            >
                <Icon
                    icon="material-symbols:logo-dev-outline"
                    class="w-16 h-10"
                />
            </Link>

            <!-- Collapse Button (Hamburger Icon) -->
            <button
                @click="$emit('toggleSidebar')"
                class="p-2 focus:outline-none"
            >
                <div class="space-y-1">
                    <span class="block w-6 h-0.5 bg-white"></span>
                    <span class="block w-6 h-0.5 bg-white"></span>
                    <span class="block w-6 h-0.5 bg-white"></span>
                </div>
            </button>
        </div>

        <!-- Navigation Links -->
        <ul class="space-y-6 relative">

        </ul>
    </nav>
</template>
