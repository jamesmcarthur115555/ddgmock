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
        { name: "Premium Plus", price: "£499/month", features: ["All Premium features", "Priority support", "Monthly equipment inspection", "10 staff training sessions"] },
        { name: "Enterprise", price: "£799/month", features: ["All Premium Plus features", "Dedicated account manager", "Weekly check-ins", "Custom training programs", "Advanced analytics"] }
    ]
};
</script>

<template>
    <section>
        <div class="bg-white rounded-lg shadow-md overflow-hidden p-6">
            <h2 class="text-2xl font-bold text-blue-900 mb-6"> Get the most from our
                membership</h2>
            <p className="text-gray-600 mb-6">Reduced Membership rates are now available and determined by the
                size of your practice to ensure you obtain maximum valuem, you are currently on <b>tier 3</b>:</p>

            <div class="grid grid-cols-1 gap-8">
                <div className="  p-4">

                    <div className="overflow-x-auto">
                        <table className="w-full border-collapse">
                            <thead>
                                <tr>
                                    <th
                                        className="bg-blue-900 text-white p-3 text-left font-semibold border border-gray-300">
                                        Practice Size<br />(Dental Chairs)</th>
                                    <th
                                        className="bg-blue-900 text-white p-3 text-center font-semibold border border-gray-300">
                                        1</th>
                                    <th
                                        className="bg-blue-900 text-white p-3 text-center font-semibold border border-gray-300">
                                        2</th>
                                    <th
                                        className="bg-blue-900 text-white p-3 text-center font-semibold border border-gray-300 bg-blue-700">
                                        3</th>
                                    <th
                                        className="bg-blue-900 text-white p-3 text-center font-semibold border border-gray-300">
                                        4</th>
                                    <th
                                        className="bg-blue-900 text-white p-3 text-center font-semibold border border-gray-300">
                                        5</th>
                                    <th
                                        className="bg-blue-900 text-white p-3 text-center font-semibold border border-gray-300">
                                        6</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td className="p-3 font-medium border border-gray-300">Annual Membership Fee</td>
                                    <td className="p-3 text-center border border-gray-300">£199</td>
                                    <td className="p-3 text-center border border-gray-300">£249</td>
                                    <td className="p-3 text-center border border-gray-300 bg-blue-100">£299</td>
                                    <td className="p-3 text-center border border-gray-300">£349</td>
                                    <td className="p-3 text-center border border-gray-300">£379</td>
                                    <td className="p-3 text-center border border-gray-300">£399</td>
                                </tr>
                                <tr>
                                    <td className="bg-blue-900 text-white p-3 font-semibold border border-gray-300"
                                        colSpan="7">Potential Annual Savings</td>
                                </tr>
                                <tr>
                                    <td className="p-3 border border-gray-300">Engineering</td>
                                    <td className="p-3 text-center border border-gray-300">£246</td>
                                    <td className="p-3 text-center border border-gray-300">£420</td>
                                    <td className="p-3 text-center border border-gray-300 bg-blue-100">£556</td>
                                    <td className="p-3 text-center border border-gray-300">£634</td>
                                    <td className="p-3 text-center border border-gray-300">£851</td>
                                    <td className="p-3 text-center border border-gray-300">£1,024</td>
                                </tr>
                                <tr>
                                    <td className="p-3 border border-gray-300">Training</td>
                                    <td className="p-3 text-center border border-gray-300">£360</td>
                                    <td className="p-3 text-center border border-gray-300">£360</td>
                                    <td className="p-3 text-center border border-gray-300 bg-blue-100">£360</td>
                                    <td className="p-3 text-center border border-gray-300">£360</td>
                                    <td className="p-3 text-center border border-gray-300">£360</td>
                                    <td className="p-3 text-center border border-gray-300">£360</td>
                                </tr>
                                <tr>
                                    <td className="p-3 border border-gray-300">Compliance</td>
                                    <td className="p-3 text-center border border-gray-300">£340</td>
                                    <td className="p-3 text-center border border-gray-300">£340</td>
                                    <td className="p-3 text-center border border-gray-300 bg-blue-100">£340</td>
                                    <td className="p-3 text-center border border-gray-300">£340</td>
                                    <td className="p-3 text-center border border-gray-300">£340</td>
                                    <td className="p-3 text-center border border-gray-300">£340</td>
                                </tr>
                                <tr>
                                    <td className="p-3 border border-gray-300">Free Compliance Consultation</td>
                                    <td className="p-3 text-center border border-gray-300 text-blue-600">£40</td>
                                    <td className="p-3 text-center border border-gray-300 text-blue-600">£40</td>
                                    <td className="p-3 text-center border border-gray-300 text-blue-600 bg-blue-100">£40
                                    </td>
                                    <td className="p-3 text-center border border-gray-300 text-blue-600">£40</td>
                                    <td className="p-3 text-center border border-gray-300 text-blue-600">£40</td>
                                    <td className="p-3 text-center border border-gray-300 text-blue-600">£40</td>
                                </tr>
                                <tr>
                                    <td className="p-3 bg-blue-900 text-white font-semibold border border-gray-300">
                                        Total Savings</td>
                                    <td className="p-3 text-center border border-gray-300 font-semibold">£986</td>
                                    <td className="p-3 text-center border border-gray-300 font-semibold">£1,160</td>
                                    <td className="p-3 text-center border border-gray-300 font-semibold bg-blue-100">
                                        £1,296</td>
                                    <td className="p-3 text-center border border-gray-300 font-semibold">£1,374</td>
                                    <td className="p-3 text-center border border-gray-300 font-semibold">£1,591</td>
                                    <td className="p-3 text-center border border-gray-300 font-semibold">£1,764</td>
                                </tr>
                                <tr>
                                    <td className="p-3 bg-blue-900 text-white font-semibold border border-gray-300">
                                        Value (Savings - Membership Fee)</td>
                                    <td className="p-3 text-center border border-gray-300 font-semibold">£787</td>
                                    <td className="p-3 text-center border border-gray-300 font-semibold">£911</td>
                                    <td className="p-3 text-center border border-gray-300 font-semibold bg-blue-100">
                                        £997</td>
                                    <td className="p-3 text-center border border-gray-300 font-semibold">£1,025</td>
                                    <td className="p-3 text-center border border-gray-300 font-semibold">£1,212</td>
                                    <td className="p-3 text-center border border-gray-300 font-semibold">£1,365</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>

            <!-- Upgrade Options -->
            <div class="mt-10">
                <h3 class="text-xl font-semibold text-gray-800 mb-6">Upgrade Options</h3>
                <p>You can upgrade the number of chairs by simply clicking the button below</p>

                <div class="mt-6 text-center">
                    <button
                        class="inline-flex items-center px-4 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm text-white bg-blue-600 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
                        Get an Upgrade Quote
                    </button>
                </div>
            </div>
        </div>
    </section>
</template>