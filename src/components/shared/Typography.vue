<template>
    <component :is="props.is" :class="[variantStyleName, weightStyleName]">
        <slot></slot>
    </component>
</template>

<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps({
    variant: {
        type: String, 
        required: true,
        validator: (value: string) => [
            "display-2xl", 
            "display-xl",
            "display-lg",
            "display-md",
            "display-sm",
            "display-xs",
            "text-xl",
            "text-lg",
            "text-md",
            "text-sm",
            "text-xs",
        ].includes(value)
    },
    is: {
        type: String, 
        default: "p",
        validator: (value: string) => [
            "h1", 
            "h2", 
            "h3", 
            "h4", 
            "h5", 
            "h6", 
            "p"
        ].includes(value)
    },
    weight: {
        type: String,
        default: "regular",
        validator: (value: string) => ["regular", "medium", "semibold", "bold"].includes(value)
    }
})

const variantStyleName = computed(() => {
    return "typography-" + props.variant
})
const weightStyleName = computed(() => {
    return "typography-weight-" + props.weight
})
</script>