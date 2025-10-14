<script setup>
import { Head, Link } from '@inertiajs/vue3';
</script>

<template>
  <Head title="Welcome to CareConnect" />

  <div class="min-h-screen flex flex-col items-center justify-center bg-gradient-to-b from-gray-900 to-gray-800 text-white">
    <div class="text-center px-6">
      <img
        src="/images/csu-logo.png"
        alt="CSU Logo"
        class="mx-auto w-24 mb-6"
        @error="$event.target.style.display='none'"
      />

      <h1 class="text-4xl font-bold mb-3">
        Welcome to <span class="text-amber-400">CareConnect</span>
      </h1>
      <p class="text-gray-300 max-w-xl mx-auto mb-8">
        A Peer Support Group Referral System designed for <b>Caraga State University</b>.
        Connect. Support. Empower. — because mental well-being matters.
      </p>

      <div class="flex justify-center gap-4">
        <Link
          href="/login"
          class="px-5 py-2 rounded-xl bg-amber-500 hover:bg-amber-600 text-white font-medium transition"
        >
          Login
        </Link>
        <Link
          href="/register"
          class="px-5 py-2 rounded-xl border border-amber-400 hover:bg-amber-500 hover:text-white transition"
        >
          Register
        </Link>
      </div>
    </div>

    <footer class="absolute bottom-4 text-gray-400 text-sm">
      © 2025 CareConnect | Developed for Caraga State University
    </footer>
  </div>
</template>
