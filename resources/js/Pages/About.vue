<script setup>
import { Head, Link } from "@inertiajs/vue3";

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
    laravelVersion: {
        type: String,
        required: true,
    },
    phpVersion: {
        type: String,
        required: true,
    },
});
</script>
<template>
    <div class="min-h-screen flex flex-col">
        <!-- Navigation Section -->
        <nav
            v-if="canLogin"
            class="bg-gradient-to-b from-gray-500 to-gray-800 pr-4 py-4 flex justify-end"
        >
            <Link
                v-if="$page.props.auth.user"
                :href="route('dashboard')"
                class="rounded-md px-3 py-2 text-white transition hover:bg-gray-600 focus:outline-none focus-visible:ring-2 focus-visible:ring-blue-400"
            >
                Dashboard
            </Link>

            <template v-else>
                <Link
                    :href="route('login')"
                    class="rounded-md px-3 py-2 text-white transition hover:bg-gray-600 focus:outline-none focus-visible:ring-2 focus-visible:ring-blue-400"
                >
                    Log in
                </Link>

                <Link
                    v-if="canRegister"
                    :href="route('register')"
                    class="ml-4 rounded-md px-3 py-2 text-white transition hover:bg-gray-600 focus:outline-none focus-visible:ring-2 focus-visible:ring-blue-400"
                >
                    Register
                </Link>
            </template>
        </nav>

        <!-- Header Section -->
        <header
            class="bg-gradient-to-b from-gray-800 to-black text-white py-16"
        >
            <div class="container mx-auto text-center">
                <h1 class="text-4xl md:text-5xl font-bold mb-4">
                    Hey, I'm Robert
                </h1>
                <p class="text-lg md:text-xl max-w-2xl mx-auto">
                    A web developer passionate about building cool stuff and
                    solving real-world problems with code.
                </p>
            </div>
        </header>

        <!-- About Me Section -->
        <section class="bg-white py-16">
            <div class="container mx-auto text-center">
                <h2 class="text-3xl font-bold mb-8">A Little Bit About Me</h2>
                <p class="text-lg max-w-3xl mx-auto mb-4">
                    I'm a 25-year-old software developer with a passion for
                    creating awesome web applications. Over the last few years,
                    I've been diving deep into technologies like JavaScript,
                    Vue.js, Node.js, and AWS. Whether it's front-end magic with
                    Vue or wrangling back-end APIs, I love making the web more
                    fun and functional.
                </p>
            </div>
        </section>

        <!-- Skills Section with Hover Animation -->
        <section class="bg-gray-100 py-16">
            <div class="container mx-auto text-center">
                <h2 class="text-3xl font-bold mb-8">What I Do</h2>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                    <!-- Skill 1 -->
                    <div
                        class="p-6 bg-white rounded-lg shadow-lg border border-gray-300 transform transition-transform duration-300 hover:scale-105 hover:shadow-xl hover:border-gray-800"
                    >
                        <h3 class="text-xl font-semibold mb-4">
                            Web Development
                        </h3>
                        <p>
                            From building modern front-ends with Vue.js to
                            designing scalable APIs, I've got you covered.
                        </p>
                    </div>

                    <!-- Skill 2 -->
                    <div
                        class="p-6 bg-white rounded-lg shadow-lg border border-gray-300 transform transition-transform duration-300 hover:scale-105 hover:shadow-xl hover:border-gray-800"
                    >
                        <h3 class="text-xl font-semibold mb-4">AWS & Cloud</h3>
                        <p>
                            Deploying web apps and managing cloud infrastructure
                            on AWS is where I thrive.
                        </p>
                    </div>

                    <!-- Skill 3 -->
                    <div
                        class="p-6 bg-white rounded-lg shadow-lg border border-gray-300 transform transition-transform duration-300 hover:scale-105 hover:shadow-xl hover:border-gray-800"
                    >
                        <h3 class="text-xl font-semibold mb-4">
                            Problem Solving
                        </h3>
                        <p>
                            I’m all about finding efficient, creative solutions
                            to coding challenges.
                        </p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Fun Facts Section -->
        <section class="bg-white py-16">
            <div class="container mx-auto text-center">
                <h2 class="text-3xl font-bold mb-8">Fun Facts About Me</h2>
                <p class="text-lg max-w-3xl mx-auto mb-4">
                    🌱 I'm constantly trying new things - right now, I'm getting
                    into freelancing.
                </p>
                <p class="text-lg max-w-3xl mx-auto mb-4">
                    🎮 I'm a huge gaming fan and love diving into automation
                    games.
                </p>
                <p class="text-lg max-w-3xl mx-auto mb-4">
                    ☕ Coffee keeps me going, especially when I'm in the middle
                    of debugging!
                </p>
            </div>
        </section>

        <!-- Footer Section -->
        <footer class="bg-gray-900 text-white py-8">
            <div class="container mx-auto text-center">
                <p>&copy; 2024 Robert Duncan. All rights reserved.</p>
                <p class="text-sm mt-2">
                    <!-- <router-link to="/privacy" class="hover:underline"
                        >Privacy Policy</router-link
                    >
                    |
                    <router-link to="/terms" class="hover:underline"
                        >Terms of Service</router-link
                    > -->
                </p>
            </div>
        </footer>
    </div>
</template>
