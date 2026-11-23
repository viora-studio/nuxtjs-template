<script setup lang="ts">
import type { PrimitiveProps } from 'reka-ui'
import type { CSSProperties, HTMLAttributes } from 'vue'
import type { ButtonVariants } from '.'
import { cn } from '~/lib/utils'
import { Primitive } from 'reka-ui'
import { computed } from 'vue'
import { buttonVariants } from '.'

interface Props extends PrimitiveProps {
  variant?: ButtonVariants['variant']
  size?: ButtonVariants['size']
  class?: HTMLAttributes['class']
  style?: CSSProperties
}

const props = withDefaults(defineProps<Props>(), {
  as: 'button',
  variant: 'default',
  size: 'default',
})

const emphasisStyles = {
  default: {
    token: 'var(--primary)',
  },
  destructive: {
    token: 'var(--destructive-strong)',
  },
} as const

const emphasisStyle = computed<CSSProperties | undefined>(() => {
  const emphasis =
    props.variant && props.variant in emphasisStyles
      ? emphasisStyles[props.variant as keyof typeof emphasisStyles]
      : undefined

  if (!emphasis)
    return undefined

  const { token } = emphasis

  return {
    '--button-emphasis-ring': `color-mix(in oklch, ${token}, black 10%)`,
    '--button-emphasis-bg': `color-mix(in oklch, ${token}, white 30%)`,
    '--button-emphasis-gradient-start': `color-mix(in oklch, ${token}, white 15%)`,
    '--button-emphasis-gradient-end': token,
    ...props.style,
  } as CSSProperties
})

</script>

<template>
  <Primitive
    data-slot="button"
    :data-variant="variant"
    :data-size="size"
    :as="as"
    :as-child="asChild"
    :class="cn(buttonVariants({ variant, size }), props.class)"
    :style="emphasisStyle ?? props.style"
    v-bind="$attrs"
  >
    <slot />
  </Primitive>
</template>
