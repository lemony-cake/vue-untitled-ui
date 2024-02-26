<template>
    <button :class="['vui-button', props.size]" :style="styles">
        <slot></slot>
    </button>
</template>

<script setup lang="ts">
import { computed  } from 'vue'

const props = defineProps({
    size: {
        type: String, 
        default: "sm",
        validator: (value: string) => [
            "sm", 
            "md",
            "lg",
            "xl",
            "xxl",
        ].includes(value)
    },
    color: { type: String, required: true },
    textColor: { type: String, required: true },
    borderColor: { type: String, required: false }
})

const styles = computed(() => {
    return {
        'background-color': props.color,
        'color': props.textColor,
        'border': props.borderColor ? `1px solid ${props.borderColor}` : 'unset'
    }
})
</script>

<style lang="less">
.vui-button {
    border-radius: 8px;
    
    &.sm {
        padding: 8px 14px;
    }

    &.md {
        padding: 10px 16px;
    }

    &.lg {
        padding: 10px 18px;
    }

    &.xl {
        padding: 12px 20px;
    }

    &.xxl {
        padding: 16px 28px;
    }
}
</style>