<template>
    <Head title="Users"></Head>
    <main>
      <div class="mx-auto max-w-7xl py-6 sm:px-6 lg:px-8">
        <div class="px-4 sm:px-6 lg:px-8">
    <div class="sm:flex sm:items-center">
      <div class="sm:flex-auto">
        <h1 class="text-xl font-semibold text-gray-900">Users</h1>
        <p class="mt-2 text-sm text-gray-700">A list of all the users in your account including their name, title, email and role.</p>
      </div>
      <div class="mt-4 sm:mt-0 sm:ml-16 sm:flex-none">
        <input v-model="search" type="text" placeholder="Search..." class="border py-2 px-4 rounded-lg" />
        <!-- <button type="button" class="inline-flex items-center justify-center rounded-md border border-transparent bg-indigo-600 px-4 py-2 text-sm font-medium text-white shadow-sm hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2 sm:w-auto">Add user</button> -->
      </div>
    </div>
    <div class="mt-8 flex flex-col">
      <div class="-my-2 -mx-4 overflow-x-auto sm:-mx-6 lg:-mx-8">
        <div class="inline-block min-w-full py-2 align-middle md:px-6 lg:px-8">
          <div class="overflow-hidden shadow ring-1 ring-black ring-opacity-5 md:rounded-lg">
            <table class="min-w-full divide-y divide-gray-300">
              <thead class="bg-gray-50">
                <tr>
                  <th scope="col" class="py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-6">Name</th>
                  <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">Email</th>
                  <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">Created at</th>
                  <th scope="col" class="relative py-3.5 pl-3 pr-4 sm:pr-6">
                    <span class="sr-only">Edit</span>
                  </th>
                </tr>
              </thead>
              <tbody class="divide-y divide-gray-200 bg-white">
                <tr v-for="user in users.data" :key="user.id">
                  <td class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-6">{{ user.name }}</td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ user.email }}</td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ user.created_at }}</td>
                  <td class="relative whitespace-nowrap py-4 pl-3 pr-4 text-right text-sm font-medium sm:pr-6">
                    <Link :href="'/users/' + user.id + 'edit'" class="text-indigo-600 hover:text-indigo-900"
                      >Edit<span class="sr-only">, {{ user.name }}</span></Link
                    >
                  </td>
                </tr>
              </tbody>
            </table>
            <Pagination :links="users.links" :users="users" class="mt-4" />
          </div>
        </div>
      </div>
    </div>
        </div>

      </div>
    </main>
</template>

<script>
import Layout from '../Shared/Layout.vue';
import { Link, Head } from '@inertiajs/vue3'
import Pagination from '../Shared/Pagination.vue'

export default {
    components: { Link, Layout, Head, Pagination },
    layout: Layout,

    props: { users: Object, filters: Object },
    data() {
        return {
            search: this.$props.filters.search,
      }
    },

    watch: {
    search(value) {
        this.$inertia.get('/users', { search: value }, { preserveState: true, replace: true });
    }
  },
    // watch(search, value => {
    //     console.log('changed ' + value)
    // })

}
</script>
