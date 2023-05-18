<template>
    <Head title="Home"></Head>
    <main>
      <div class="mx-auto max-w-7xl py-6 sm:px-6 lg:px-8">
        <Link href="/modal" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Modal</Link>
      </div>
    </main>
</template>

<script>
import Layout from '../Shared/Layout.vue';
import { Head, Link } from '@inertiajs/vue3'
export default {
    components: { Head, Link },
    layout: Layout
}
</script>
