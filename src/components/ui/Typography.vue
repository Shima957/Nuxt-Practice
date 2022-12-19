<script lang="ts" setup>
  const TypographyVariants = ['h1', 'h2', 'h3', 'h4', 'h5', 'h6', 'p', 'span'] as const
  type TypographyVariantsType = typeof TypographyVariants[number]
  type Props = {
    variants?: TypographyVariantsType;
    center?: boolean;
    bold?:boolean;
  }

  const props = withDefaults(defineProps<Props>(), {
    variants: 'span',
  })

  const classnames = computed(() => {
    return {
      'center': props.center,
      'bold': props.bold
    }
  })
</script>

<template>
  <component :is="variants" :class="classnames">
    <slot />
  </component>
</template>

<style lang="scss">
.center {
  text-align: center;
}

.bold {
  font-weight: bold;
}
</style>