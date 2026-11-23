<script setup lang="ts">
import type { AlertDialogActionProps } from 'reka-ui'
import type { CSSProperties, HTMLAttributes } from 'vue'
import type { ButtonVariants } from '@/components/ui/button'
import { reactiveOmit } from '@vueuse/core'
import { cn } from '~/lib/utils'
import { AlertDialogAction } from 'reka-ui'
import { computed } from 'vue'
import { buttonVariants } from '@/components/ui/button'

const props = withDefaults(
  defineProps<AlertDialogActionProps & {
    class?: HTMLAttributes['class']
    style?: CSSProperties
    variant?: ButtonVariants['variant']
    size?: ButtonVariants['size']
  }>(),
  {
    variant: 'default',
    size: 'default',
  },
)

const delegatedProps = reactiveOmit(props, 'class', 'style', 'variant', 'size')

const emphasisStyle = computed<CSSProperties | undefined>(() => {
  const token =
    props.variant === 'default'
      ? 'var(--primary)'
      : props.variant === 'destructive'
        ? 'var(--destructive-strong)'
        : undefined

  if (!token)
    return props.style

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
  <AlertDialogAction
    data-slot="alert-dialog-action"
    v-bind="delegatedProps"
    :class="cn('', buttonVariants({ variant, size }), props.class)"
    :style="emphasisStyle"
  >
    <slot />
  </AlertDialogAction>
</template>
