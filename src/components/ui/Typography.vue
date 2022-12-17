<script lang="ts" setup>
  const TypographyVariants = ['h1', 'h2', 'h3', 'h4', 'h5', 'h6', 'p', 'span'] as const
  type TypographyVariantsType = typeof TypographyVariants[number]
  type Props = {
    variants?: TypographyVariantsType
  }

  const prop = withDefaults(defineProps<Props>(), {
    variants: 'span'
  })
</script>

<template>
  <component :is="variants">
    <slot />
  </component>
</template>