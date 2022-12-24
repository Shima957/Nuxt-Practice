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

  const variantStyle = computed(() => {
    switch(props.variants) {
      case 'h1':
        return 'heading-one'

      case 'h2':
        return 'heading-two'

      case 'h3':
        return 'heading-three'

      case 'h4':
        return 'subtitle'

      case 'h5':
        return 'subtitle'

      case 'h6':
        return 'subtitle'

      case 'p':
        return 'body'

      default:
        return 'normal'
    }
  })
</script>

<template>
  <component :is="variants" :class="[classnames, variantStyle]">
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

.heading-one {
  font-size: 51px;
}

.heading-two {
  font-size: 30px;
}

.heading-three {
  font-size: 24px;
}

.subtitle {
  font-size: 20px;
}

.body {
  font-size: 14px;
}

.normal {
  font-size: 12px;
}
</style>
