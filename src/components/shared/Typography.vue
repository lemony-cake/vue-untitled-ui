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
            "p",
            "span"
        ].includes(value)
    },
    weight: {
        type: String,
        default: "regular",
        validator: (value: string) => ["regular", "medium", "semibold", "bold"].includes(value)
    }
})

const variantStyleName = computed(() => {
    return "vui-typography-" + props.variant
})
const weightStyleName = computed(() => {
    return "vui-typography-weight-" + props.weight
})
</script>

<style lang="less">
@font-family: Inter, sans-serif;

@weight-regular: 400;
@weight-medium: 500;
@weight-semibold: 600;
@weight-bold: 700;

@2p-track: {
    letter-spacing: -0.02em;
}

// --- Weighting ---
.vui-typography-weight-regular {
    font-weight: @weight-regular;
}

.vui-typography-weight-medium {
    font-weight: @weight-medium;
}

.vui-typography-weight-semibold {
    font-weight: @weight-semibold;
}

.vui-typography-weight-bold {
    font-weight: @weight-bold;
}

// --- Display typography ---
.vui-typography-display-2xl {
    font-family: @font-family;
    @2p-track();
    font-size: 72px;
    line-height: 90px;
}

.vui-typography-display-xl {
    font-family: @font-family;
    @2p-track();
    font-size: 60px;
    line-height: 72px;
}

.vui-typography-display-lg {
    font-family: @font-family;
    @2p-track();
    font-size: 48px;
    line-height: 60px;
}

.vui-typography-display-md {
    font-family: @font-family;
    @2p-track();
    font-size: 36px;
    line-height: 44px;
}

.vui-typography-display-sm {
    font-family: @font-family;
    font-size: 30px;
    line-height: 38px;
}

.vui-typography-display-xs {
    font-family: @font-family;
    font-size: 24px;
    line-height: 32px;
}

// --- Text typography ---
.vui-typography-text-xl {
    font-family: @font-family;
    font-size: 20px;
    line-height: 30px;
}

.vui-typography-text-lg {
    font-family: @font-family;
    font-size: 18px;
    line-height: 28px;
}

.vui-typography-text-md {
    font-family: @font-family;
    font-size: 16px;
    line-height: 24px;
}

.vui-typography-text-sm {
    font-family: @font-family;
    font-size: 14px;
    line-height: 20px;
}

.vui-typography-text-xs {
    font-family: @font-family;
    font-size: 12px;
    line-height: 18px;
}
</style>