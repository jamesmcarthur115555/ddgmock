<script setup>
import { ref } from 'vue';

// We'll keep the data but remove the toggle functionality
const membership = {
    status: "Premium",
    expiryDate: "December 31, 2023",
    services: [
        { name: "24/7 Technical Support", used: false },
        { name: "Quarterly Equipment Inspection", used: true },
        { name: "Staff Training Sessions (3/5)", used: false },
        { name: "Compliance Audit", used: true },
        { name: "Marketing Consultation", used: false }
    ],
    upgradeOptions: [
        { name: "Premium Plus", price: "$499/month", features: ["All Premium features", "Priority support", "Monthly equipment inspection", "10 staff training sessions"] },
        { name: "Enterprise", price: "$799/month", features: ["All Premium Plus features", "Dedicated account manager", "Weekly check-ins", "Custom training programs", "Advanced analytics"] }
    ]
};
</script>

<template>
    <section>
        <div class="bg-white rounded-lg shadow-md overflow-hidden p-6">
            <h2 class="text-2xl font-bold text-blue-900 mb-6">Membership Information</h2>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <!-- Current Membership -->
                <div class="bg-blue-50 rounded-lg p-6 border border-blue-100">
                    <h3 class="text-lg font-semibold text-blue-800 mb-4">Current Plan</h3>
                    <div class="mb-4">
                        <div class="flex justify-between items-center mb-2">
                            <span class="text-sm text-gray-600">Status:</span>
                            <span class="font-medium text-blue-700">{{ membership.status }}</span>
                        </div>
                        <div class="flex justify-between items-center">
                            <span class="text-sm text-gray-600">Expiry Date:</span>
                            <span class="font-medium text-blue-700">{{ membership.expiryDate }}</span>
                        </div>
                    </div>
                    <button
                        class="w-full mt-4 inline-flex justify-center items-center px-4 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm text-white bg-blue-600 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
                        Renew Membership
                    </button>
                </div>

                <!-- Services -->
                <div class="bg-white rounded-lg p-6 border border-gray-200">
                    <h3 class="text-lg font-semibold text-gray-800 mb-4">Included Services</h3>
                    <ul class="space-y-3">
                        <li v-for="(service, index) in membership.services" :key="index" class="flex items-center">
                            <span v-if="service.used"
                                class="h-5 w-5 rounded-full bg-green-100 flex items-center justify-center mr-3">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-3 w-3 text-green-600" fill="none"
                                    viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                        d="M5 13l4 4L19 7" />
                                </svg>
                            </span>
                            <span v-else class="h-5 w-5 rounded-full bg-gray-100 flex items-center justify-center mr-3">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-3 w-3 text-gray-400" fill="none"
                                    viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                        d="M12 6v6m0 0v6m0-6h6m-6 0H6" />
                                </svg>
                            </span>
                            <span class="text-sm text-gray-700">{{ service.name }}</span>
                        </li>
                    </ul>
                    <button
                        class="w-full mt-4 inline-flex justify-center items-center px-4 py-2 border border-blue-600 text-sm font-medium rounded-md text-blue-600 bg-white hover:bg-blue-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
                        Request Service
                    </button>
                </div>

                <!-- Billing History -->
                <div class="bg-white rounded-lg p-6 border border-gray-200">
                    <h3 class="text-lg font-semibold text-gray-800 mb-4">Billing History</h3>
                    <ul class="space-y-3">
                        <li class="border-b pb-2">
                            <div class="flex justify-between items-center">
                                <span class="text-sm font-medium">Oct 1, 2023</span>
                                <span class="text-sm text-gray-600">$399.00</span>
                            </div>
                            <p class="text-xs text-gray-500">Premium Membership - Monthly</p>
                        </li>
                        <li class="border-b pb-2">
                            <div class="flex justify-between items-center">
                                <span class="text-sm font-medium">Sep 1, 2023</span>
                                <span class="text-sm text-gray-600">$399.00</span>
                            </div>
                            <p class="text-xs text-gray-500">Premium Membership - Monthly</p>
                        </li>
                        <li>
                            <div class="flex justify-between items-center">
                                <span class="text-sm font-medium">Aug 1, 2023</span>
                                <span class="text-sm text-gray-600">$399.00</span>
                            </div>
                            <p class="text-xs text-gray-500">Premium Membership - Monthly</p>
                        </li>
                    </ul>
                    <button
                        class="w-full mt-4 inline-flex justify-center items-center px-4 py-2 border border-gray-300 text-sm font-medium rounded-md text-gray-700 bg-white hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
                        View All Transactions
                    </button>
                </div>
            </div>

            <!-- Upgrade Options -->
            <div class="mt-10">
                <h3 class="text-xl font-semibold text-gray-800 mb-6">Upgrade Options</h3>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <div v-for="(option, index) in membership.upgradeOptions" :key="index"
                        class="bg-white rounded-lg border border-gray-200 p-6 hover:shadow-md transition-shadow">
                        <h4 class="text-lg font-medium text-blue-800">{{ option.name }}</h4>
                        <p class="text-2xl font-bold text-gray-900 my-2">{{ option.price }}</p>
                        <ul class="mt-4 space-y-2">
                            <li v-for="(feature, fIndex) in option.features" :key="fIndex" class="flex items-start">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-green-500 mr-2 mt-0.5"
                                    fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                        d="M5 13l4 4L19 7" />
                                </svg>
                                <span class="text-sm text-gray-600">{{ feature }}</span>
                            </li>
                        </ul>
                        <button
                            class="mt-4 w-full inline-flex justify-center items-center px-4 py-2 border border-blue-600 text-sm font-medium rounded-md text-blue-600 bg-white hover:bg-blue-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
                            Upgrade
                        </button>
                    </div>
                </div>
                <div class="mt-6 text-center">
                    <button
                        class="inline-flex items-center px-4 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm text-white bg-blue-600 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
                        Get a Custom Quote
                    </button>
                </div>
            </div>
        </div>
    </section>
</template>