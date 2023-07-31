<template>
    <AppLayout title="Edit">
        <template #header>
            <div class="flex">
                <h2 class="flex-1 font-semibold text-xl text-gray-200 leading-tight">Edit</h2>
                <Link class="bg-green-500 text-white font-semibold py-2 px-4 border border-gray-700 rounded mb-2" as="button" :href="'/patients/' + patient.id">Back</Link>
            </div>
        </template>

        <div class="py-6">
            <div class="bg-white max-w-4xl p-4 mx-auto rounded-lg border">
            <form @submit.prevent="submit" class="flex flex-wrap">
                <div class="">
                <h4 class="text-xl mb-4">Edit</h4>

                        <div class="form-field">
                            <label for="name">Name</label>
                            <input type="text" id="name" v-model="form.name" class="input-field" />
                        </div>

                        <div class="form-field">
                            <label for="address">Address</label>
                            <input type="text" id="address" v-model="form.address" class="input-field" />
                        </div>

                        <div class="form-field">
                            <label for="age">Age</label>
                            <input type="number" id="age" v-model="form.age" class="input-field" />
                        </div>

                        <div class="form-field">
                            <label for="weight">Weight</label>
                            <input type="text" id="weight" v-model="form.weight" class="input-field" />
                        </div>

                        <div class="form-field">
                            <label for="height">Height</label>
                            <input type="text" id="height" v-model="form.height" class="input-field" />
                        </div>

                        <div class="form-field">
                            <label for="email">Email</label>
                            <input type="email" id="email" v-model="form.email" class="input-field" />
                        </div>

                        <div class="mt-auto flex justify-end">
                            <button class="bg-green-500 text-white font-semibold py-2 px-4 border border-gray-700 rounded mb-2" type="submit">Save Changes</button>
                        </div>
                    </div>
                </form>
            </div>
        </div>
    </AppLayout>
</template>

<script setup>
    import AppLayout from '@/Layouts/AppLayout.vue';
    import { Head, Link, useForm } from '@inertiajs/vue3';

    const props = defineProps({
        patient: Object
    })

    const form = useForm({
        name: props.patient.name,
        address: props.patient.address,
        age: props.patient.age,
        weight: props.patient.weight,
        height: props.patient.height,
        email: props.patient.email,
    })

    function submit() {
        form.patch('/patients/' + props.patient.id)
    }
</script>
