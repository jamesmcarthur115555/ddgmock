<script setup>
import { ref } from 'vue';
import CustomerInfoSection from './CustomerInfoSection.vue';
import MembershipSection from './MembershipSection.vue';
import TrainingComplianceHub from './TrainingComplianceHub.vue';
import InventoryManagement from './InventoryManagement.vue';
import CommunicationsCenter from './CommunicationsCenter.vue';

const activeTab = ref('dashboard');

const setActiveTab = (tab) => {
  activeTab.value = tab;
};
</script>

<template>
  <div class="ddg-portal bg-gray-50 min-h-screen">
    <!-- Header -->
    <header class="bg-white shadow-sm">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-4 flex justify-between items-center">
        <div class="flex items-center">
          <div class="h-10 w-10 bg-blue-600 rounded-md flex items-center justify-center text-white font-bold text-xl">
            DDG</div>
          <h1 class="ml-4 text-2xl font-semibold text-blue-800">Customer Portal</h1>
        </div>
        <div class="flex items-center">
          <button class="text-gray-600 hover:text-blue-800 mr-4">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24"
              stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9" />
            </svg>
          </button>
          <div class="relative">
            <button class="flex items-center text-gray-700 hover:text-blue-800">
              <div class="h-8 w-8 rounded-full bg-gray-300 flex items-center justify-center text-gray-600">DS</div>
              <span class="ml-2">Dr. Smith</span>
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" viewBox="0 0 20 20" fill="currentColor">
                <path fill-rule="evenodd"
                  d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z"
                  clip-rule="evenodd" />
              </svg>
            </button>
          </div>
        </div>
      </div>
    </header>

    <!-- Navigation -->
    <nav class="bg-white border-b border-gray-200">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex space-x-8">
          <button @click="setActiveTab('dashboard')"
            class="py-4 px-3 inline-flex items-center text-sm font-medium border-b-2 transition-colors"
            :class="activeTab === 'dashboard' ? 'border-blue-500 text-blue-600' : 'border-transparent text-gray-500 hover:text-gray-700 hover:border-gray-300'">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" fill="none" viewBox="0 0 24 24"
              stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6" />
            </svg>
            Dashboard
          </button>
          <button @click="setActiveTab('membership')"
            class="py-4 px-3 inline-flex items-center text-sm font-medium border-b-2 transition-colors"
            :class="activeTab === 'membership' ? 'border-blue-500 text-blue-600' : 'border-transparent text-gray-500 hover:text-gray-700 hover:border-gray-300'">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" fill="none" viewBox="0 0 24 24"
              stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M10 6H5a2 2 0 00-2 2v9a2 2 0 002 2h14a2 2 0 002-2V8a2 2 0 00-2-2h-5m-4 0V5a2 2 0 114 0v1m-4 0a2 2 0 104 0m-5 8a2 2 0 100-4 2 2 0 000 4zm0 0c1.306 0 2.417.835 2.83 2M9 14a3.001 3.001 0 00-2.83 2M15 11h3m-3 4h2" />
            </svg>
            Membership
          </button>
          <button @click="setActiveTab('training')"
            class="py-4 px-3 inline-flex items-center text-sm font-medium border-b-2 transition-colors"
            :class="activeTab === 'training' ? 'border-blue-500 text-blue-600' : 'border-transparent text-gray-500 hover:text-gray-700 hover:border-gray-300'">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" fill="none" viewBox="0 0 24 24"
              stroke="currentColor">
              <path d="M12 14l9-5-9-5-9 5 9 5z" />
              <path
                d="M12 14l6.16-3.422a12.083 12.083 0 01.665 6.479A11.952 11.952 0 0012 20.055a11.952 11.952 0 00-6.824-2.998 12.078 12.078 0 01.665-6.479L12 14z" />
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M12 14l9-5-9-5-9 5 9 5zm0 0l6.16-3.422a12.083 12.083 0 01.665 6.479A11.952 11.952 0 0012 20.055a11.952 11.952 0 00-6.824-2.998 12.078 12.078 0 01.665-6.479L12 14zm-4 6v-7.5l4-2.222" />
            </svg>
            Training & Compliance
          </button>
          <button @click="setActiveTab('inventory')"
            class="py-4 px-3 inline-flex items-center text-sm font-medium border-b-2 transition-colors"
            :class="activeTab === 'inventory' ? 'border-blue-500 text-blue-600' : 'border-transparent text-gray-500 hover:text-gray-700 hover:border-gray-300'">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" fill="none" viewBox="0 0 24 24"
              stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M20 7l-8-4-8 4m16 0l-8 4m8-4v10l-8 4m0-10L4 7m8 4v10M4 7v10l8 4" />
            </svg>
            Inventory
          </button>
        </div>
      </div>
    </nav>

    <!-- Main Content -->
    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
      <!-- Dashboard View -->
      <div v-if="activeTab === 'dashboard'" class="grid grid-cols-1 lg:grid-cols-3 gap-8">
        <!-- Left Column -->
        <div class="lg:col-span-2 space-y-8">
          <CustomerInfoSection />
          <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
            <div class="bg-white rounded-lg shadow-md p-6">
              <h2 class="text-lg font-semibold text-gray-800 mb-4">Quick Stats</h2>
              <div class="grid grid-cols-2 gap-4">
                <div class="bg-blue-50 p-4 rounded-lg">
                  <p class="text-sm text-gray-500">Active Training</p>
                  <p class="text-2xl font-bold text-blue-600">2</p>
                </div>
                <div class="bg-green-50 p-4 rounded-lg">
                  <p class="text-sm text-gray-500">Compliance Status</p>
                  <p class="text-2xl font-bold text-green-600">Good</p>
                </div>
                <div class="bg-purple-50 p-4 rounded-lg">
                  <p class="text-sm text-gray-500">Inventory Items</p>
                  <p class="text-2xl font-bold text-purple-600">43</p>
                </div>
                <div class="bg-yellow-50 p-4 rounded-lg">
                  <p class="text-sm text-gray-500">Pending Repairs</p>
                  <p class="text-2xl font-bold text-yellow-600">2</p>
                </div>
              </div>
            </div>
            <div class="bg-white rounded-lg shadow-md p-6">
              <h2 class="text-lg font-semibold text-gray-800 mb-4">Upcoming Due Dates</h2>
              <ul class="space-y-3">
                <li class="flex justify-between items-center p-3 bg-red-50 rounded-lg">
                  <span class="text-sm font-medium">OSHA Compliance Update</span>
                  <span class="text-xs text-red-600 font-medium">Nov 15, 2023</span>
                </li>
                <li class="flex justify-between items-center p-3 bg-yellow-50 rounded-lg">
                  <span class="text-sm font-medium">Advanced Sterilization</span>
                  <span class="text-xs text-yellow-600 font-medium">Dec 5, 2023</span>
                </li>
                <li class="flex justify-between items-center p-3 bg-blue-50 rounded-lg">
                  <span class="text-sm font-medium">Membership Renewal</span>
                  <span class="text-xs text-blue-600 font-medium">Dec 31, 2023</span>
                </li>
              </ul>
            </div>
          </div>
        </div>

        <!-- Right Column -->
        <div class="space-y-8">
          <CommunicationsCenter />
        </div>
      </div>

      <!-- Membership View -->
      <div v-if="activeTab === 'membership'" class="space-y-8">
        <MembershipSection />
      </div>

      <!-- Training & Compliance View -->
      <div v-if="activeTab === 'training'" class="space-y-8">
        <TrainingComplianceHub />
      </div>

      <!-- Inventory View -->
      <div v-if="activeTab === 'inventory'" class="space-y-8">
        <InventoryManagement />
      </div>
    </main>

    <!-- Footer -->
    <footer class="bg-blue-900 text-white mt-12">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div>
            <h3 class="text-lg font-semibold mb-4">Contact DDG</h3>
            <p class="mb-2">1234 Dental Drive</p>
            <p class="mb-2">Suite 100</p>
            <p class="mb-2">Dental City, DC 12345</p>
            <p class="mb-2">Phone: (555) 123-4567</p>
            <p>Email: support@ddgdental.com</p>
          </div>
          <div>
            <h3 class="text-lg font-semibold mb-4">Quick Links</h3>
            <ul class="space-y-2">
              <li><a href="#" class="hover:text-blue-300">About DDG</a></li>
              <li><a href="#" class="hover:text-blue-300">Services</a></li>
              <li><a href="#" class="hover:text-blue-300">Products</a></li>
              <li><a href="#" class="hover:text-blue-300">Support</a></li>
              <li><a href="#" class="hover:text-blue-300">FAQs</a></li>
            </ul>
          </div>
          <div>
            <h3 class="text-lg font-semibold mb-4">Legal</h3>
            <ul class="space-y-2">
              <li><a href="#" class="hover:text-blue-300">Privacy Policy</a></li>
              <li><a href="#" class="hover:text-blue-300">Terms of Service</a></li>
              <li><a href="#" class="hover:text-blue-300">Cookie Policy</a></li>
            </ul>
          </div>
        </div>
        <div class="border-t border-blue-800 mt-8 pt-8 text-center">
          <p>&copy; 2023 DDG Dental Group. All rights reserved.</p>
        </div>
      </div>
    </footer>
  </div>
</template>
