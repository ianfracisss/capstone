<script setup lang="ts">
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/vue3';

// Optional breadcrumb data (if you added breadcrumb support)
const breadcrumbs = [
  { label: 'Home', href: '/dashboard' },
  { label: 'Dashboard' },
];
</script>

<template>
  <Head title="Dashboard | CareConnect" />

  <AuthenticatedLayout :breadcrumbs="breadcrumbs">
    <template #header>
      <h2 class="text-3xl font-bold leading-tight text-green-800">
        CareConnect Dashboard
      </h2>
      <p class="text-gray-600 text-sm mt-1">
        Overview of CSU Peer Support Group Referral System
      </p>
    </template>

    <!-- Dashboard content -->
    <div class="mt-6 space-y-6">
      <!-- Stats Cards -->
      <div class="grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
        <div class="bg-white rounded-xl shadow p-5 border border-gray-200">
          <h3 class="text-sm font-semibold text-gray-500 uppercase">Active Referrals</h3>
          <p class="mt-3 text-3xl font-bold text-green-700">42</p>
          <p class="text-xs text-gray-400 mt-1">+8 this week</p>
        </div>

        <div class="bg-white rounded-xl shadow p-5 border border-gray-200">
          <h3 class="text-sm font-semibold text-gray-500 uppercase">Support Groups</h3>
          <p class="mt-3 text-3xl font-bold text-green-700">12</p>
          <p class="text-xs text-gray-400 mt-1">Updated daily</p>
        </div>

        <div class="bg-white rounded-xl shadow p-5 border border-gray-200">
          <h3 class="text-sm font-semibold text-gray-500 uppercase">Pending Requests</h3>
          <p class="mt-3 text-3xl font-bold text-green-700">5</p>
          <p class="text-xs text-gray-400 mt-1">Needs follow-up</p>
        </div>
      </div>

      <!-- Charts or Tables Section -->
      <div class="bg-white rounded-xl shadow p-6 border border-gray-200">
        <h3 class="text-lg font-semibold text-gray-700 mb-4">Recent Activities</h3>
        <div class="border-t border-gray-100 pt-4">
          <ul class="divide-y divide-gray-100">
            <li class="py-2 flex justify-between">
              <span class="text-gray-700 text-sm">New referral added by Student Council</span>
              <span class="text-gray-400 text-xs">2 hours ago</span>
            </li>
            <li class="py-2 flex justify-between">
              <span class="text-gray-700 text-sm">Peer Support Session scheduled for Psychology Dept</span>
              <span class="text-gray-400 text-xs">Yesterday</span>
            </li>
            <li class="py-2 flex justify-between">
              <span class="text-gray-700 text-sm">Referral closed by Guidance Office</span>
              <span class="text-gray-400 text-xs">2 days ago</span>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </AuthenticatedLayout>
</template>
