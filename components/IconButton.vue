<template>
  <button type="button" class="icon-button" :class="{ 'icon-button--light': light }">
    <IconCarbon:menu v-if="type === 'menu' && !isNavOpen" />
    <IconCarbon:close v-if="(type === 'menu' && isNavOpen) || type === 'close'" />
  </button>
</template>

<script setup lang="ts">
interface Props {
  type?: 'menu' | 'close' | string;
  isNavOpen?: boolean;
  light?: boolean;
}

withDefaults(defineProps<Props>(), {
  type: 'menu',
  isNavOpen: false,
  light: false,
});
</script>

<style lang="scss" scoped>
.icon-button {
  @include flex($justify: center, $align: center, $gap: 0);
  width: 4rem;
  height: 4rem;
  padding: 0.5rem;
  background-color: transparent;
  border: 0.2rem solid transparent;
  border-radius: 0.5rem;
  cursor: pointer;
  transition: all 0.3s ease-in-out;

  svg {
    color: $navy;
    font-size: 3rem;
    transition: all 0.3s ease-in-out;
  }

  @media (hover: hover) {
    &:hover {
      svg {
        color: $white;
      }
      cursor: pointer;
    }
  }

  &--light {
    svg {
      color: $white;
      font-size: 3rem;
      transition: all 0.3s ease-in-out;
    }

    @media (hover: hover) {
      &:hover {
        svg {
          color: $navy;
        }
        cursor: pointer;
      }
    }
  }
}
</style>
