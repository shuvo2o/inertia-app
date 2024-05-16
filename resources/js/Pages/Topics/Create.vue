<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, Link, useForm } from '@inertiajs/vue3'; // Ensure useForm is imported from @inertiajs/vue3

const form = useForm({
  name: null,
  image: null,
})

function storeTopic() {
  form.post('/topics')
}
</script>

<template>
  <Head title="Topics" />

  <AuthenticatedLayout>
    <div class="container mx-auto p-4">
      <div class="flex justify-end m-2 p-2">
        <Link href="/topics/create" class="px-4 py-2 bg-indigo-500 hover:bg-indigo-500 text-white rounded">Back</Link>
      </div>
      <div class="">
        <div class="grid place-content-center mt-10">
          <form @submit.prevent="storeTopic" class="bg-white shadow-md m-2 p-2 rounded">
            <div class="sm:col-span-4">
              <label for="title" class="block text-sm font-medium text-gray-700 rounded">Name</label>
              <div class="mt-1">
                <input type="text" id="title" name="title" v-model="form.name" class="block w-full transition duration-150 ease-in-out rounded appearance-none bg-white border border-grey-400">
              </div>
            </div>
            <div class="sm:col-span-4">
              <label for="image" class="block text-sm font-medium text-gray-700 rounded">Image</label>
              <div class="mt-1">
                <input type="file" id="image" name="image" @input="form.image = $event.target.files[0]" class="block w-full transition duration-150 ease-in-out rounded">
              </div>
            </div>
            <div class="m-2 p-2">
              <button type="submit" class="px-4 p-2 rounded bg-green-400 hover:bg-green-600 text-white">Create</button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </AuthenticatedLayout>
</template>
