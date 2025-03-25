<script setup>
import { ref } from 'vue';

const isExpanded = ref(false);
const toggleExpand = () => {
    isExpanded.value = !isExpanded.value;
};

const customerInfo = {
    practiceName: "Bright Smile Dental Clinic",
    lead: "Dr. Jane Smith",
    address: "123 Dental Avenue, Suite 200, Oral City, OC 54321",
    phone: "(555) 987-6543",
    email: "info@brightsmile.com"
};
</script>

<template>
    <section class="bg-white rounded-lg shadow-md overflow-hidden">
        <div class="p-6">
            <div class="flex justify-between items-center">
                <h2 class="text-2xl font-bold text-blue-900">{{ customerInfo.practiceName }}</h2>
                <button @click="toggleExpand" class="text-blue-600 hover:text-blue-800 flex items-center">
                    <span>{{ isExpanded ? 'Hide Details' : 'My Details' }}</span>
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1 transition-transform"
                        :class="{ 'transform rotate-180': isExpanded }" viewBox="0 0 20 20" fill="currentColor">
                        <path fill-rule="evenodd"
                            d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z"
                            clip-rule="evenodd" />
                    </svg>
                </button>
            </div>

            <transition enter-active-class="transition duration-300 ease-out"
                enter-from-class="transform -translate-y-4 opacity-0"
                enter-to-class="transform translate-y-0 opacity-100"
                leave-active-class="transition duration-200 ease-in"
                leave-from-class="transform translate-y-0 opacity-100"
                leave-to-class="transform -translate-y-4 opacity-0">
                <div v-if="isExpanded" class="mt-6 border-t pt-4">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <h3 class="text-sm font-medium text-gray-500">Practice Lead</h3>
                            <p class="mt-1 text-base text-gray-900">{{ customerInfo.lead }}</p>
                        </div>
                        <div>
                            <h3 class="text-sm font-medium text-gray-500">Address</h3>
                            <p class="mt-1 text-base text-gray-900">{{ customerInfo.address }}</p>
                        </div>
                        <div>
                            <h3 class="text-sm font-medium text-gray-500">Phone</h3>
                            <p class="mt-1 text-base text-gray-900">{{ customerInfo.phone }}</p>
                        </div>
                        <div>
                            <h3 class="text-sm font-medium text-gray-500">Email</h3>
                            <p class="mt-1 text-base text-gray-900">{{ customerInfo.email }}</p>
                        </div>
                    </div>
                    <div class="mt-6 flex justify-end">
                        <button
                            class="inline-flex items-center px-4 py-2 border border-blue-600 text-sm font-medium rounded-md text-blue-600 bg-white hover:bg-blue-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
                            Request Information Update
                        </button>
                    </div>
                </div>
            </transition>
        </div>
    </section>
</template>