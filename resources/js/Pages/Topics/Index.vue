<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, Link } from '@inertiajs/vue3';

const props = defineProps({
  topics: Array
})
</script>

<template>

  <Head title="Topics" />

  <AuthenticatedLayout>
    <div class="container mx-auto p-4">
      <div class="flex justify-end m-2 p-2">
        <Link href="/topics/create" class="px-4 py-2 bg-indigo-500 hover:bg-indigo-500 text-white rounded ">Create
        </Link>
      </div>
      <table class="table-auto w-full  border-collapse border border-gray-300">
        <thead>
          <tr class="bg-cyan-400 text-dark-black">
            <th class="border border-gray-300 px-4 py-2 ">Title</th>
            <th class="border border-gray-300 px-4 py-2">Image</th>
            <th class="border border-gray-300 px-4 py-2"></th>
            <th scope="col" class="relative px-6 py-3">
              <span class="sr-only">Edit</span>
              
            </th>

          </tr>
        </thead>
        <tbody>
          <tr v-for="topic in topics" :key="topic.id" class="bg-blue-100">
            <td class="border border-gray-300 text-center px-4 py-2">{{ topic.name }}</td>
            <td class="border border-gray-300  px-4 py-2">
              <img :src="topic.image" class="w-12 h-12 rounded" alt="">
            </td>
            <td class="border border-gray-300 text-center  px-4 py-2">
              <a :href="`/topics/${topic.id}/edit`" class="text-indigo-600 hover:text-indigo-900">
                Edit
              </a>
            </td>
            <td class="border border-gray-300 text-center  px-4 py-2">
              <a :href="`/topics/${topic.id}`" method="delete" as="button" type="button" class="text-indigo-600 hover:text-indigo-900" >
                Delete
              </a>
            </td>

          </tr>
          <tr class="bg-blue-100">

          </tr>

        </tbody>
      </table>
    </div>
  </AuthenticatedLayout>
</template>
