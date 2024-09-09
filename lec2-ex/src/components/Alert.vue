<script setup>
import {computed} from "vue";

const props = defineProps({
    message: String,
    type: {
        type: String,
        default: 'info'
    }
})
const wrapperClasses = computed(() => {
    return {
        alert: true,
        [`alert--${props.type}`]: props.type,
    }
})
</script>

<template>
    <div :class="wrapperClasses" role="alert">
        {{ message }}
    </div>
</template>

<style lang="scss">
.alert {
    &--info {
        @apply p-4 mb-4 text-sm text-blue-800 rounded-lg bg-blue-50 dark:bg-gray-800 dark:text-blue-400;
    }
    &--danger{
        @apply p-4 mb-4 text-sm text-red-800 rounded-lg bg-red-50 dark:bg-gray-800 dark:text-red-400
    }
    &--success {
        @apply p-4 mb-4 text-sm text-green-800 rounded-lg bg-green-50 dark:bg-gray-800 dark:text-green-400;
    }
    &--warning {
        @apply p-4 mb-4 text-sm text-yellow-800 rounded-lg bg-yellow-50 dark:bg-gray-800 dark:text-yellow-300;
    }
    &--error {
        @apply p-4 text-sm text-gray-800 rounded-lg bg-gray-50 dark:bg-gray-800 dark:text-gray-300;
    }
}
</style>
