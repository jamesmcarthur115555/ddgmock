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

                        <div class="grid grid-cols-3  gap-4">
                            <div class="border rounded-lg p-4 hover:border-blue-500 hover:shadow-md transition-all
                                text-center flex flex-col items-center gap-2">
                                <h4 class="text-base font-medium text-gray-900">Remote Training Courses</h4>
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
                                    stroke-width="1.5" stroke="currentColor" class="size-6">
                                    <path stroke-linecap="round" stroke-linejoin="round"
                                        d="M9 17.25v1.007a3 3 0 0 1-.879 2.122L7.5 21h9l-.621-.621A3 3 0 0 1 15 18.257V17.25m6-12V15a2.25 2.25 0 0 1-2.25 2.25H5.25A2.25 2.25 0 0 1 3 15V5.25m18 0A2.25 2.25 0 0 0 18.75 3H5.25A2.25 2.25 0 0 0 3 5.25m18 0V12a2.25 2.25 0 0 1-2.25 2.25H5.25A2.25 2.25 0 0 1 3 12V5.25" />
                                </svg>



                            </div>

                            <div class="border rounded-lg p-4 hover:border-blue-500 hover:shadow-md transition-all
                                text-center flex flex-col items-center gap-2">
                                <h4 class="text-base font-medium text-gray-900">In Practice Training Courses</h4>
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
                                    stroke-width="1.5" stroke="currentColor" class="size-6">
                                    <path stroke-linecap="round" stroke-linejoin="round"
                                        d="M2.25 21h19.5m-18-18v18m10.5-18v18m6-13.5V21M6.75 6.75h.75m-.75 3h.75m-.75 3h.75m3-6h.75m-.75 3h.75m-.75 3h.75M6.75 21v-3.375c0-.621.504-1.125 1.125-1.125h2.25c.621 0 1.125.504 1.125 1.125V21M3 3h12m-.75 4.5H21m-3.75 3.75h.008v.008h-.008v-.008Zm0 3h.008v.008h-.008v-.008Zm0 3h.008v.008h-.008v-.008Z" />
                                </svg>



                            </div>

                            <div class="border rounded-lg p-4 hover:border-blue-500 hover:shadow-md transition-all
                                text-center flex flex-col items-center gap-2">
                                <h4 class="text-base font-medium text-gray-900">Off Site Training Courses</h4>
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
                                    stroke-width="1.5" stroke="currentColor" class="size-6">
                                    <path stroke-linecap="round" stroke-linejoin="round"
                                        d="M4.26 10.147a60.438 60.438 0 0 0-.491 6.347A48.62 48.62 0 0 1 12 20.904a48.62 48.62 0 0 1 8.232-4.41 60.46 60.46 0 0 0-.491-6.347m-15.482 0a50.636 50.636 0 0 0-2.658-.813A59.906 59.906 0 0 1 12 3.493a59.903 59.903 0 0 1 10.399 5.84c-.896.248-1.783.52-2.658.814m-15.482 0A50.717 50.717 0 0 1 12 13.489a50.702 50.702 0 0 1 7.74-3.342M6.75 15a.75.75 0 1 0 0-1.5.75.75 0 0 0 0 1.5Zm0 0v-3.675A55.378 55.378 0 0 1 12 8.443m-7.007 11.55A5.981 5.981 0 0 0 6.75 15.75v-1.5" />
                                </svg>


                            </div>
                        </div>

                    </div>

                </div>

                <!-- Compliance Tab -->
                <div v-if="activeTab === 'compliance'">
                    <h2 class="text-xl font-bold text-gray-800 mb-6">Compliance Management</h2>

                    <div class="mb-8">
                        <div class="flex justify-between items-center mb-4">
                            <h3 class="text-lg font-medium text-gray-900">Certificates & Licenses</h3>
                            <button @click="openAddDialog"
                                class="text-sm text-blue-600 hover:text-blue-800 font-medium flex items-center gap-2">
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
                                    stroke-width="1.5" stroke="currentColor" class="size-6">
                                    <path stroke-linecap="round" stroke-linejoin="round"
                                        d="M12 16.5V9.75m0 0 3 3m-3-3-3 3M6.75 19.5a4.5 4.5 0 0 1-1.41-8.775 5.25 5.25 0 0 1 10.233-2.33 3 3 0 0 1 3.758 3.848A3.752 3.752 0 0 1 18 19.5H6.75Z" />
                                </svg>
                                Upload Doc
                            </button>
                        </div>

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

                <div class="grid grid-cols-4 gap-2">

                    <div class="mt-8 p-4 bg-blue-50 border border-blue-200 rounded-lg col-span-3 ">
                        <h4 class="font-medium text-blue-800">Special Membership Offer</h4>
                        <p class="mt-1 text-sm text-blue-700">Upgrade to Premium Plus and receive a complimentary annual
                            compliance audit worth $1,200.</p>
                        <button class="mt-3 text-sm bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">
                            Learn More
                        </button>
                    </div>

                    <div class="mt-8 p-4 border border-black-400 rounded-lg col-span-1 ">
                        <h4 class="font-medium text-blue-800">Compliance Policies</h4>
                        <p class="mt-1 text-sm text-blue-700"></p>
                        <button class="mt-3 text-sm bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">
                            Shop Now
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>