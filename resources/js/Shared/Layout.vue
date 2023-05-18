<template>
    <Head title="Aplicação Inertia" />
    <Nav />
    <Header />
    <slot />
    <Modal />
</template>
<script>
import Nav from "./Nav.vue";
import Header from "./Head.vue";
import { Head } from "@inertiajs/vue3"
import { Modal } from 'momentum-modal'
export default {
    components: { Nav, Header, Head, Modal}
}
</script>
<style lang="">

</style>
