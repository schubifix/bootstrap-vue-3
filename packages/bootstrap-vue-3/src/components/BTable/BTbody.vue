<template>
  <tbody role="rowgroup" :class="classes">
    <slot />
  </tbody>
</template>

<script setup lang="ts">
// import type {BTBodyProps} from '../../types/components'
import type {ColorVariant} from '../../types'
import {computed} from 'vue'

interface BTBodyProps {
  variant?: ColorVariant
}

const props = defineProps<BTBodyProps>()

const classes = computed(() => ({
  [`thead-${props.variant}`]: props.variant !== undefined,
}))
</script>
