<script setup>
import { ref } from 'vue';

const isExpanded = ref(false);
const toggleExpand = () => {
    isExpanded.value = !isExpanded.value;
};

const inventory = {
    items: [
        { id: 1, name: "Dental Chair", category: "Large Equipment", quantity: 4, lastServiced: "Aug 15, 2023" },
        { id: 2, name: "Autoclave", category: "Small Equipment", quantity: 2, lastServiced: "Sep 10, 2023" },
        { id: 3, name: "Dental Handpieces", category: "Small Equipment", quantity: 12, lastServiced: "Oct 5, 2023" },
        { id: 4, name: "Composite Material", category: "Consumables", quantity: 25, lastServiced: "N/A" }
    ],
    categories: [
        { name: "Large Equipment", link: "#" },
        { name: "Small Equipment", link: "#" },
        { name: "Consumables", link: "#" }
    ]
};

const repairRequests = [
    { id: 1, item: "X-Ray Machine", status: "In Progress", submitted: "Oct 12, 2023" },
    { id: 2, item: "Dental Chair #2", status: "Scheduled", submitted: "Oct 8, 2023" }
];
</script>

<template>
    <section class="bg-white rounded-lg shadow-md overflow-hidden">
        <div class="p-6">
            <div class="flex justify-between items-center">
                <h2 class="text-xl font-bold text-gray-800">Inventory Management</h2>
                <button @click="toggleExpand" class="text-blue-600 hover:text-blue-800 flex items-center">
                    <span>{{ isExpanded ? 'Hide' : 'View' }}</span>
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
                <div v-if="isExpanded" class="mt-6">
                    <div class="flex justify-between items-center mb-4">
                        <h3 class="text-lg font-medium text-gray-900">Equipment Inventory</h3>
                        <button class="text-sm text-blue-600 hover:text-blue-800 font-medium">
                            + Add Item
                        </button>
                    </div>

                    <div class="overflow-x-auto">
                        <table class="min-w-full divide-y divide-gray-200">
                            <thead class="bg-gray-50">
                                <tr>
                                    <th scope="col"
                                        class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                                        Item
                                    </th>
                                    <th scope="col"
                                        class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                                        Category
                                    </th>
                                    <th scope="col"
                                        class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                                        Quantity
                                    </th>
                                    <th scope="col"
                                        class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                                        Last Serviced
                                    </th>
                                    <th scope="col" class="relative px-6 py-3">
                                        <span class="sr-only">Actions</span>
                                    </th>
                                </tr>
                            </thead>
                            <tbody class="bg-white divide-y divide-gray-200">
                                <tr v-for="item in inventory.items" :key="item.id">
                                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">
                                        {{ item.name }}
                                    </td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                                        {{ item.category }}
                                    </td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                                        {{ item.quantity }}
                                    </td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                                        {{ item.lastServiced }}
                                    </td>
                                    <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">
                                        <button class="text-blue-600 hover:text-blue-900 mr-3">Edit</button>
                                        <button class="text-red-600 hover:text-red-900">Delete</button>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>

                    <div class="mt-8">
                        <h3 class="text-lg font-medium text-gray-900 mb-4">Purchasing Links</h3>
                        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                            <div v-for="(category, index) in inventory.categories" :key="index"
                                class="border rounded-lg p-4 hover:border-blue-500 hover:shadow-md transition-all text-center">
                                <h4 class="text-base font-medium text-gray-900">{{ category.name }}</h4>
                                <a :href="category.link"
                                    class="mt-2 inline-block text-blue-600 hover:text-blue-800 font-medium">
                                    Browse Catalog
                                </a>
                            </div>
                        </div>
                    </div>

                    <div class="mt-8">
                        <h3 class="text-lg font-medium text-gray-900 mb-4">Repair Requests</h3>
                        <div class="bg-gray-50 rounded-lg p-4">
                            <ul class="divide-y divide-gray-200">
                                <li v-for="request in repairRequests" :key="request.id"
                                    class="py-3 flex justify-between items-center">
                                    <div>
                                        <p class="text-sm font-medium text-gray-900">{{ request.item }}</p>
                                        <p class="text-xs text-gray-500">Submitted: {{ request.submitted }}</p>
                                    </div>
                                    <div class="flex items-center">
                                        <span class="px-2.5 py-0.5 rounded-full text-xs font-medium"
                                            :class="request.status === 'In Progress' ? 'bg-yellow-100 text-yellow-800' : 'bg-green-100 text-green-800'">
                                            {{ request.status }}
                                        </span>
                                        <button class="ml-4 text-blue-600 hover:text-blue-800 text-sm">
                                            Details
                                        </button>
                                    </div>
                                </li>
                            </ul>
                        </div>
                        <div class="mt-4 text-center">
                            <button
                                class="inline-flex items-center px-4 py-2 border border-blue-600 text-sm font-medium rounded-md text-blue-600 bg-white hover:bg-blue-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
                                Submit New Repair Request
                            </button>
                        </div>
                    </div>
                </div>
            </transition>
        </div>
    </section>
</template>