<template>
  <component :is="footerTag" class="card-footer" :class="[footerClass, classes]">
    <!-- eslint-disable-next-line vue/no-v-html -->
    <div v-if="!!footerHtml" v-html="footerHtml" />
    <slot v-else>
      {{ footer }}
    </slot>
  </component>
</template>

<script setup lang="ts">
// import type {BCardFooterProps} from '../../types/components'
import type {ColorVariant, TextColorVariant} from '../../types'
import {computed} from 'vue'

interface BCardFooterProps {
  footer?: string
  footerBgVariant?: ColorVariant
  footerBorderVariant?: ColorVariant
  footerClass?: Array<string> | Record<string, boolean | undefined | null> | string
  footerHtml?: string
  footerTag?: string
  footerTextVariant?: TextColorVariant
}

const props = withDefaults(defineProps<BCardFooterProps>(), {
  footerTag: 'div',
})

const classes = computed(() => ({
  [`text-${props.footerTextVariant}`]: props.footerTextVariant !== undefined,
  [`bg-${props.footerBgVariant}`]: props.footerBgVariant !== undefined,
  [`border-${props.footerBorderVariant}`]: props.footerBorderVariant !== undefined,
}))
</script>
