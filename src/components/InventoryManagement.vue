<script setup>
import { ref } from 'vue';

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

const repairRequests = ref([
    { id: 1, item: "X-Ray Machine", status: "In Progress", submitted: "Oct 12, 2023" },
    { id: 2, item: "Dental Chair #2", status: "Scheduled", submitted: "Oct 8, 2023" }
]);

// Dialog state
const showAddDialog = ref(false);
const showEditDialog = ref(false);
const showRepairDialog = ref(false);
const currentItem = ref(null);
const newItem = ref({
    id: null,
    name: '',
    category: '',
    quantity: 0,
    lastServiced: ''
});

const newRepairRequest = ref({
    id: null,
    item: '',
    status: 'Pending',
    submitted: '',
    description: '',
    priority: 'Medium'
});

// Open edit dialog with item data
const openEditDialog = (item) => {
    currentItem.value = { ...item };
    showEditDialog.value = true;
};

// Open add dialog
const openAddDialog = () => {
    newItem.value = {
        id: Math.max(0, ...inventory.items.map(item => item.id)) + 1,
        name: '',
        category: '',
        quantity: 0,
        lastServiced: ''
    };
    showAddDialog.value = true;
};

// Save edited item
const saveEdit = () => {
    const index = inventory.items.findIndex(item => item.id === currentItem.value.id);
    if (index !== -1) {
        inventory.items[index] = { ...currentItem.value };
    }
    showEditDialog.value = false;
};

// Add new item
const addItem = () => {
    inventory.items.push({ ...newItem.value });
    showAddDialog.value = false;
};

// Delete item
const deleteItem = (id) => {
    const index = inventory.items.findIndex(item => item.id === id);
    if (index !== -1) {
        inventory.items.splice(index, 1);
    }
};

// Open repair request dialog
const openRepairDialog = () => {
    const today = new Date();
    const formattedDate = today.toLocaleDateString('en-US', {
        year: 'numeric',
        month: 'short',
        day: 'numeric'
    });

    newRepairRequest.value = {
        id: Math.max(0, ...repairRequests.value.map(req => req.id)) + 1,
        item: '',
        status: 'Pending',
        submitted: formattedDate,
        description: '',
        priority: 'Medium'
    };
    showRepairDialog.value = true;
};

// Submit repair request
const submitRepairRequest = () => {
    repairRequests.value.push({ ...newRepairRequest.value });
    showRepairDialog.value = false;
};
</script>

<template>
    <section class="bg-white rounded-lg shadow-md overflow-hidden">
        <div class="p-6">
            <div class="flex justify-between items-center">
                <h2 class="text-xl font-bold text-gray-800">Inventory Management</h2>
            </div>

            <div class="mt-6">
                <div class="flex justify-between items-center mb-4">
                    <h3 class="text-lg font-medium text-gray-900">Equipment Inventory</h3>


                    <div class="flex items-end gap-2">
                        <button @click="openAddDialog" class="text-sm text-blue-600 hover:text-blue-800 font-medium">
                            + Add Item
                        </button>


                    </div>
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
                                    <button @click="openEditDialog(item)"
                                        class="text-blue-600 hover:text-blue-900 mr-3">Edit</button>
                                    <button @click="deleteItem(item.id)"
                                        class="text-red-600 hover:text-red-900">Delete</button>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                    <div class="mt-4 flex justify-end">

                        <button @click="exportInventory"
                            class="inline-flex items-center px-4 py-2 flex gap-2 items-center border border-blue-600 text-sm font-medium rounded-md text-blue-600 bg-white hover:bg-blue-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                                stroke="currentColor" class="size-5">
                                <path stroke-linecap="round" stroke-linejoin="round"
                                    d="M9 8.25H7.5a2.25 2.25 0 0 0-2.25 2.25v9a2.25 2.25 0 0 0 2.25 2.25h9a2.25 2.25 0 0 0 2.25-2.25v-9a2.25 2.25 0 0 0-2.25-2.25H15M9 12l3 3m0 0 3-3m-3 3V2.25" />
                            </svg>
                            Export Inventory
                        </button>
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
                                    <span class="px-2.5 py-0.5 rounded-full text-xs font-medium" :class="{
                                        'bg-yellow-100 text-yellow-800': request.status === 'In Progress',
                                        'bg-green-100 text-green-800': request.status === 'Scheduled',
                                        'bg-gray-100 text-gray-800': request.status === 'Pending',
                                        'bg-blue-100 text-blue-800': request.status === 'Completed'
                                    }">
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
                        <button @click="openRepairDialog"
                            class="inline-flex items-center px-4 py-2 border border-blue-600 text-sm font-medium rounded-md text-blue-600 bg-white hover:bg-blue-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
                            Submit New Repair Request
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Add Item Dialog -->
    <div v-if="showAddDialog" class="fixed inset-0 bg-gray-600 bg-opacity-50 flex items-center justify-center z-50">
        <div class="bg-white rounded-lg shadow-xl p-6 w-full max-w-md">
            <h3 class="text-lg font-medium text-gray-900 mb-4">Add New Item</h3>
            <form @submit.prevent="addItem">
                <div class="mb-4">
                    <label class="block text-sm font-medium text-gray-700 mb-1">Name</label>
                    <input v-model="newItem.name" type="text" required
                        class="w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500">
                </div>
                <div class="mb-4">
                    <label class="block text-sm font-medium text-gray-700 mb-1">Category</label>
                    <select v-model="newItem.category" required
                        class="w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500">
                        <option v-for="category in inventory.categories" :key="category.name" :value="category.name">
                            {{ category.name }}
                        </option>
                    </select>
                </div>
                <div class="mb-4">
                    <label class="block text-sm font-medium text-gray-700 mb-1">Quantity</label>
                    <input v-model.number="newItem.quantity" type="number" min="0" required
                        class="w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500">
                </div>
                <div class="mb-4">
                    <label class="block text-sm font-medium text-gray-700 mb-1">Last Serviced</label>
                    <input v-model="newItem.lastServiced" type="text" placeholder="N/A for consumables"
                        class="w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500">
                </div>
                <div class="flex justify-end space-x-3">
                    <button type="button" @click="showAddDialog = false"
                        class="px-4 py-2 border border-gray-300 rounded-md shadow-sm text-sm font-medium text-gray-700 bg-white hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
                        Cancel
                    </button>
                    <button type="submit"
                        class="px-4 py-2 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-blue-600 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
                        Add Item
                    </button>
                </div>
            </form>
        </div>
    </div>

    <!-- Edit Item Dialog -->
    <div v-if="showEditDialog" class="fixed inset-0 bg-gray-600 bg-opacity-50 flex items-center justify-center z-50">
        <div class="bg-white rounded-lg shadow-xl p-6 w-full max-w-md">
            <h3 class="text-lg font-medium text-gray-900 mb-4">Edit Item</h3>
            <form @submit.prevent="saveEdit">
                <div class="mb-4">
                    <label class="block text-sm font-medium text-gray-700 mb-1">Name</label>
                    <input v-model="currentItem.name" type="text" required
                        class="w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500">
                </div>
                <div class="mb-4">
                    <label class="block text-sm font-medium text-gray-700 mb-1">Category</label>
                    <select v-model="currentItem.category" required
                        class="w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500">
                        <option v-for="category in inventory.categories" :key="category.name" :value="category.name">
                            {{ category.name }}
                        </option>
                    </select>
                </div>
                <div class="mb-4">
                    <label class="block text-sm font-medium text-gray-700 mb-1">Quantity</label>
                    <input v-model.number="currentItem.quantity" type="number" min="0" required
                        class="w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500">
                </div>
                <div class="mb-4">
                    <label class="block text-sm font-medium text-gray-700 mb-1">Last Serviced</label>
                    <input v-model="currentItem.lastServiced" type="text" placeholder="N/A for consumables"
                        class="w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500">
                </div>
                <div class="flex justify-end space-x-3">
                    <button type="button" @click="showEditDialog = false"
                        class="px-4 py-2 border border-gray-300 rounded-md shadow-sm text-sm font-medium text-gray-700 bg-white hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
                        Cancel
                    </button>
                    <button type="submit"
                        class="px-4 py-2 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-blue-600 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
                        Save Changes
                    </button>
                </div>
            </form>
        </div>
    </div>

    <!-- Repair Request Dialog -->
    <div v-if="showRepairDialog" class="fixed inset-0 bg-gray-600 bg-opacity-50 flex items-center justify-center z-50">
        <div class="bg-white rounded-lg shadow-xl p-6 w-full max-w-md">
            <h3 class="text-lg font-medium text-gray-900 mb-4">Submit Repair Request</h3>
            <form @submit.prevent="submitRepairRequest">
                <div class="mb-4">
                    <label class="block text-sm font-medium text-gray-700 mb-1">Equipment Name</label>
                    <input v-model="newRepairRequest.item" type="text" required
                        class="w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500">
                </div>
                <div class="mb-4">
                    <label class="block text-sm font-medium text-gray-700 mb-1">Description of Issue</label>
                    <textarea v-model="newRepairRequest.description" rows="3" required
                        class="w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500"></textarea>
                </div>
                <div class="mb-4">
                    <label class="block text-sm font-medium text-gray-700 mb-1">Priority</label>
                    <select v-model="newRepairRequest.priority" required
                        class="w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500">
                        <option value="Low">Low</option>
                        <option value="Medium">Medium</option>
                        <option value="High">High</option>
                        <option value="Urgent">Urgent</option>
                    </select>
                </div>
                <div class="flex justify-end space-x-3">
                    <button type="button" @click="showRepairDialog = false"
                        class="px-4 py-2 border border-gray-300 rounded-md shadow-sm text-sm font-medium text-gray-700 bg-white hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
                        Cancel
                    </button>
                    <button type="submit"
                        class="px-4 py-2 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-blue-600 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
                        Submit Request
                    </button>
                </div>
            </form>
        </div>
    </div>
</template>