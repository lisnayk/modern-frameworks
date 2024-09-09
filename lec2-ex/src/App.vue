<script setup>

import Navigation from "@/components/Navigation.vue";
import Alert from "@/components/Alert.vue";
</script>

<template>
    <Navigation/>
    <main class="container mx-auto">
        <div class="flex flex-col p-4">
            <Alert v-for="type in ['info','danger', 'warning', 'success', 'error']" :key="type" :message="`This is an ${type} alert`" :type="type"/>
        </div>
    </main>

</template>
