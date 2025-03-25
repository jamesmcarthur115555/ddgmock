<script setup>
import { ref } from 'vue';

const activeTab = ref('training');
const setActiveTab = (tab) => {
    activeTab.value = tab;
};

const trainingData = {
    active: [
        { id: 1, title: "OSHA Compliance Update", type: "Remote", dueDate: "Nov 15, 2023", progress: 25 },
        { id: 2, title: "Advanced Sterilization Techniques", type: "In-Practice", dueDate: "Dec 5, 2023", progress: 50 }
    ],
    completed: [
        { id: 3, title: "Radiation Safety", type: "Offsite", completedDate: "Aug 10, 2023" },
        { id: 4, title: "Patient Communication", type: "Remote", completedDate: "Sep 22, 2023" }
    ]
};

const complianceData = {
    certificates: [
        { id: 1, title: "OSHA Compliance", status: "Valid", expiryDate: "Mar 15, 2024" },
        { id: 2, title: "Radiation Safety", status: "Valid", expiryDate: "Jun 22, 2024" },
        { id: 3, title: "HIPAA Compliance", status: "Expiring Soon", expiryDate: "Dec 10, 2023" }
    ],
    audits: [
        { id: 1, title: "Annual Safety Inspection", status: "Passed", date: "Jul 12, 2023", score: "92%" },
        { id: 2, title: "HIPAA Security Assessment", status: "Scheduled", date: "Nov 30, 2023" }
    ]
};
</script>

<template>
    <section>
        <div class="bg-white rounded-lg shadow-md overflow-hidden">
            <div class="border-b border-gray-200">
                <div class="flex">
                    <button @click="setActiveTab('training')" class="px-6 py-4 text-sm font-medium"
                        :class="activeTab === 'training' ? 'text-blue-600 border-b-2 border-blue-500' : 'text-gray-500 hover:text-gray-700'">
                        Training
                    </button>
                    <button @click="setActiveTab('compliance')" class="px-6 py-4 text-sm font-medium"
                        :class="activeTab === 'compliance' ? 'text-blue-600 border-b-2 border-blue-500' : 'text-gray-500 hover:text-gray-700'">
                        Compliance
                    </button>
                </div>
            </div>

            <div class="p-6">
                <!-- Training Tab -->
                <div v-if="activeTab === 'training'">
                    <h2 class="text-xl font-bold text-gray-800 mb-6">Training Programs</h2>

                    <div class="mb-8">
                        <h3 class="text-lg font-medium text-gray-800 mb-4">Active Training</h3>
                        <div class="space-y-4">
                            <div v-for="training in trainingData.active" :key="training.id"
                                class="bg-white border border-gray-200 rounded-lg p-4 hover:shadow-sm transition-shadow">
                                <div class="flex justify-between items-start">
                                    <div>
                                        <h4 class="text-base font-medium text-gray-900">{{ training.title }}</h4>
                                        <div class="mt-1 flex items-center text-sm text-gray-500">
                                            <span class="mr-2">{{ training.type }}</span>
                                            <span>Due: {{ training.dueDate }}</span>
                                        </div>
                                    </div>
                                    <button class="text-blue-600 hover:text-blue-800 text-sm font-medium">
                                        Continue
                                    </button>
                                </div>
                                <div class="mt-3">
                                    <div class="flex items-center">
                                        <div class="flex-1 bg-gray-200 rounded-full h-2">
                                            <div class="bg-blue-600 h-2 rounded-full"
                                                :style="{ width: `${training.progress}%` }"></div>
                                        </div>
                                        <span class="ml-2 text-xs text-gray-500">{{ training.progress }}%</span>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <div>
                        <h3 class="text-lg font-medium text-gray-800 mb-4">Completed Training</h3>
                        <div class="space-y-4">
                            <div v-for="training in trainingData.completed" :key="training.id"
                                class="bg-white border border-gray-200 rounded-lg p-4 hover:shadow-sm transition-shadow">
                                <div class="flex justify-between items-start">
                                    <div>
                                        <h4 class="text-base font-medium text-gray-900">{{ training.title }}</h4>
                                        <div class="mt-1 flex items-center text-sm text-gray-500">
                                            <span class="mr-2">{{ training.type }}</span>
                                            <span>Completed: {{ training.completedDate }}</span>
                                        </div>
                                    </div>
                                    <div class="flex items-center">
                                        <span
                                            class="bg-green-100 text-green-800 text-xs px-2 py-1 rounded-full mr-2">Completed</span>
                                        <button class="text-blue-600 hover:text-blue-800 text-sm font-medium">
                                            Certificate
                                        </button>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="mt-8 flex justify-center">
                        <button
                            class="inline-flex items-center px-4 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm text-white bg-blue-600 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
                            Browse All Training Programs
                        </button>
                    </div>
                </div>

                <!-- Compliance Tab -->
                <div v-if="activeTab === 'compliance'">
                    <h2 class="text-xl font-bold text-gray-800 mb-6">Compliance Management</h2>

                    <div class="mb-8">
                        <h3 class="text-lg font-medium text-gray-800 mb-4">Certificates & Licenses</h3>
                        <div class="overflow-hidden shadow ring-1 ring-black ring-opacity-5 md:rounded-lg">
                            <table class="min-w-full divide-y divide-gray-300">
                                <thead class="bg-gray-50">
                                    <tr>
                                        <th scope="col"
                                            class="py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900">
                                            Certificate</th>
                                        <th scope="col"
                                            class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">Status
                                        </th>
                                        <th scope="col"
                                            class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">Expiry
                                            Date</th>
                                        <th scope="col" class="relative py-3.5 pl-3 pr-4">
                                            <span class="sr-only">Actions</span>
                                        </th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-gray-200 bg-white">
                                    <tr v-for="cert in complianceData.certificates" :key="cert.id">
                                        <td class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900">
                                            {{ cert.title }}</td>
                                        <td class="whitespace-nowrap px-3 py-4 text-sm">
                                            <span class="px-2 inline-flex text-xs leading-5 font-semibold rounded-full"
                                                :class="cert.status === 'Valid' ? 'bg-green-100 text-green-800' : 'bg-yellow-100 text-yellow-800'">
                                                {{ cert.status }}
                                            </span>
                                        </td>
                                        <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ cert.expiryDate
                                            }}</td>
                                        <td class="whitespace-nowrap py-4 pl-3 pr-4 text-right text-sm font-medium">
                                            <a href="#" class="text-blue-600 hover:text-blue-900">View</a>
                                        </td>
                                    </tr>
                                </tbody>
                            </table>
                        </div>
                    </div>

                    <div>
                        <h3 class="text-lg font-medium text-gray-800 mb-4">Compliance Audits</h3>
                        <ul class="space-y-3">
                            <li v-for="audit in complianceData.audits" :key="audit.id"
                                class="bg-white border border-gray-200 rounded-lg p-4 hover:shadow-sm transition-shadow">
                                <div class="flex justify-between items-center">
                                    <div>
                                        <h4 class="text-base font-medium text-gray-900">{{ audit.title }}</h4>
                                        <p class="text-sm text-gray-500">{{ audit.date }}</p>
                                    </div>
                                    <div class="flex items-center">
                                        <span class="px-2.5 py-0.5 rounded-full text-xs font-medium"
                                            :class="audit.status === 'Passed' ? 'bg-green-100 text-green-800' : 'bg-blue-100 text-blue-800'">
                                            {{ audit.status }}
                                        </span>
                                        <span v-if="audit.score" class="ml-2 text-sm font-medium text-gray-900">{{
                                            audit.score }}</span>
                                        <button class="ml-4 text-blue-600 hover:text-blue-800">
                                            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none"
                                                viewBox="0 0 24 24" stroke="currentColor">
                                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                                    d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" />
                                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                                    d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z" />
                                            </svg>
                                        </button>
                                    </div>
                                </div>
                            </li>
                        </ul>
                    </div>
                </div>

                <div class="mt-8 p-4 bg-blue-50 border border-blue-200 rounded-lg">
                    <h4 class="font-medium text-blue-800">Special Membership Offer</h4>
                    <p class="mt-1 text-sm text-blue-700">Upgrade to Premium Plus and receive a complimentary annual
                        compliance audit worth $1,200.</p>
                    <button class="mt-3 text-sm bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">
                        Learn More
                    </button>
                </div>
            </div>
        </div>
    </section>
</template>