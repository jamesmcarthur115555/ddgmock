<script setup>
const announcements = [
    {
        id: 1,
        title: "New Equipment Promotion",
        content: "Get 15% off on all new dental chairs and imaging equipment through December.",
        date: "Nov 2, 2023",
        type: "promotion"
    },
    {
        id: 2,
        title: "System Maintenance",
        content: "The portal will be down for maintenance on Nov 15 from 2-4 AM EST.",
        date: "Nov 5, 2023",
        type: "service"
    },
    {
        id: 3,
        title: "New Training Courses",
        content: "We've added 5 new compliance training modules. Check them out!",
        date: "Oct 28, 2023",
        type: "general"
    },
    {
        id: 4,
        title: "Holiday Hours",
        content: "Our support team will have modified hours during the upcoming holidays.",
        date: "Oct 25, 2023",
        type: "general"
    }
];
</script>

<template>
    <section class="bg-white rounded-lg shadow-md overflow-hidden">
        <div class="p-6">
            <h2 class="text-xl font-bold text-gray-800 mb-4">Communications Center</h2>

            <div class="space-y-4">
                <div v-for="announcement in announcements" :key="announcement.id"
                    class="border rounded-lg p-4 hover:shadow-sm transition-all" :class="{
                        'border-blue-200 bg-blue-50': announcement.type === 'promotion',
                        'border-yellow-200 bg-yellow-50': announcement.type === 'service',
                        'border-gray-200': announcement.type === 'general'
                    }">
                    <div class="flex justify-between items-start">
                        <h3 class="text-base font-medium text-gray-900">{{ announcement.title }}</h3>
                        <span class="text-xs text-gray-500">{{ announcement.date }}</span>
                    </div>
                    <p class="mt-2 text-sm text-gray-600">{{ announcement.content }}</p>
                    <div class="mt-3 flex justify-end">
                        <button class="text-sm text-blue-600 hover:text-blue-800">
                            Read More
                        </button>
                    </div>
                </div>
            </div>

            <div class="mt-6">
                <h3 class="text-lg font-medium text-gray-900 mb-3">Quick Actions</h3>
                <div class="grid grid-cols-2 gap-3">
                    <button class="p-3 border rounded-md hover:bg-gray-50 flex flex-col items-center justify-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-blue-600" fill="none"
                            viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                d="M8 10h.01M12 10h.01M16 10h.01M9 16H5a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v8a2 2 0 01-2 2h-5l-5 5v-5z" />
                        </svg>
                        <span class="mt-1 text-sm text-gray-700">Contact Support</span>
                    </button>
                    <button class="p-3 border rounded-md hover:bg-gray-50 flex flex-col items-center justify-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-blue-600" fill="none"
                            viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2" />
                        </svg>
                        <span class="mt-1 text-sm text-gray-700">View All Messages</span>
                    </button>
                    <button class="p-3 border rounded-md hover:bg-gray-50 flex flex-col items-center justify-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-blue-600" fill="none"
                            viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
                        </svg>
                        <span class="mt-1 text-sm text-gray-700">Schedule Call</span>
                    </button>
                    <button class="p-3 border rounded-md hover:bg-gray-50 flex flex-col items-center justify-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-blue-600" fill="none"
                            viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                d="M19 20H5a2 2 0 01-2-2V6a2 2 0 012-2h10a2 2 0 012 2v1m2 13a2 2 0 01-2-2V7m2 13a2 2 0 002-2V9a2 2 0 00-2-2h-2m-4-3H9M7 16h6M7 8h6v4H7V8z" />
                        </svg>
                        <span class="mt-1 text-sm text-gray-700">Newsletter</span>
                    </button>
                </div>
            </div>

            <div class="mt-6 p-4 bg-blue-50 border border-blue-200 rounded-lg">
                <h4 class="font-medium text-blue-800">Your Account Manager</h4>
                <div class="mt-3 flex items-center">
                    <div
                        class="h-12 w-12 rounded-full bg-blue-200 flex items-center justify-center text-blue-600 font-medium">
                        SJ</div>
                    <div class="ml-3">
                        <p class="text-sm font-medium text-gray-900">Sarah Johnson</p>
                        <p class="text-xs text-gray-500">sarah.johnson@ddgdental.com</p>
                        <p class="text-xs text-gray-500">(555) 987-6543</p>
                    </div>
                </div>
                <button class="mt-3 w-full text-sm bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">
                    Schedule Meeting
                </button>
            </div>
        </div>
    </section>
</template>