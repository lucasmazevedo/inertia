<template>
    <Link
        href="/"
        :class="{'bg-gray-900 text-white': active }"
        class="text-gray-300 hover:bg-gray-700 hover:text-white rounded-md px-3 py-2 text-sm font-medium"
    >
    <slot />
    </Link>
</template>
<script>
import { Link } from "@inertiajs/vue3";
export default {
    components: { Link },
    props: {
        active: Boolean,
    }
}
</script>
