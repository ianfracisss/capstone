<script setup>
import Checkbox from '@/Components/Checkbox.vue';
import GuestLayout from '@/Layouts/GuestLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

defineProps({
    canResetPassword: Boolean,
    status: String,
});

const form = useForm({
    email: '',
    password: '',
    remember: false,
});

const submit = () => {
    form.post(route('login'), {
        onFinish: () => form.reset('password'),
    });
};
</script>

<template>
    <GuestLayout>
        <Head title="Login | CareConnect" />

        <div class="min-h-screen flex flex-col justify-center items-center bg-gradient-to-b from-green-900 to-green-700">
            <div class="bg-white shadow-lg rounded-2xl p-8 w-full max-w-md">
                <div class="text-center mb-6">
                    <img
                        src="/images/csu-logo.png"
                        alt="CSU Logo"
                        class="w-16 mx-auto mb-3"
                        @error="$event.target.style.display='none'"
                    />
                    <h1 class="text-2xl font-bold text-green-800">CareConnect</h1>
                    <p class="text-sm text-gray-600">CSU Peer Support Group Referral System</p>
                </div>

                <div v-if="status" class="mb-4 text-sm font-medium text-green-600 text-center">
                    {{ status }}
                </div>

                <form @submit.prevent="submit">
                    <div>
                        <InputLabel for="email" value="Email Address" />
                        <TextInput
                            id="email"
                            type="email"
                            class="mt-1 block w-full"
                            v-model="form.email"
                            required
                            autofocus
                            autocomplete="username"
                        />
                        <InputError class="mt-2" :message="form.errors.email" />
                    </div>

                    <div class="mt-4">
                        <InputLabel for="password" value="Password" />
                        <TextInput
                            id="password"
                            type="password"
                            class="mt-1 block w-full"
                            v-model="form.password"
                            required
                            autocomplete="current-password"
                        />
                        <InputError class="mt-2" :message="form.errors.password" />
                    </div>

                    <div class="mt-4 flex justify-between items-center">
                        <label class="flex items-center text-sm text-gray-700">
                            <Checkbox name="remember" v-model:checked="form.remember" />
                            <span class="ms-2">Remember me</span>
                        </label>

                        <Link
                            v-if="canResetPassword"
                            :href="route('password.request')"
                            class="text-sm text-green-700 hover:underline"
                        >
                            Forgot password?
                        </Link>
                    </div>

                    <PrimaryButton
                        class="mt-6 w-full bg-green-700 hover:bg-green-800 text-white font-semibold py-2 rounded-lg transition"
                        :class="{ 'opacity-25': form.processing }"
                        :disabled="form.processing"
                    >
                        Log In
                    </PrimaryButton>

                    <p class="text-center text-sm text-gray-600 mt-4">
                        Don’t have an account?
                        <Link href="/register" class="text-green-700 hover:underline">Register</Link>
                    </p>
                </form>
            </div>

            <footer class="text-white text-sm mt-6">
                © 2025 CareConnect | Caraga State University
            </footer>
        </div>
    </GuestLayout>
</template>
