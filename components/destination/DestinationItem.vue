<template>
  <CommonButtonLineWithImg :as="as" :icon="icon" class="destination-item">
    <template #image>
      <slot name="image">
        <CommonImageLoader class="destination-item-icon" :src="iconUrl" />
      </slot>
    </template>
    <template #default>
      <CommonButtonLineBodyInfo class="text-left">
        <template #label v-if="label || $slots['label']">
          <slot name="label">{{ label }}</slot>
        </template>
        <template #underline v-if="description || $slots['underline']">
          <slot name="underline">{{ description }}</slot>
        </template>
      </CommonButtonLineBodyInfo>
    </template>
    <template #right v-if="$slots.right">
      <slot name="right" />
    </template>
  </CommonButtonLineWithImg>
</template>

<script lang="ts" setup>
import type { Component, PropType } from "vue";

defineProps({
  as: {
    type: [String, Object] as PropType<string | Component>,
  },
  label: {
    type: String,
  },
  iconUrl: {
    type: String,
  },
  description: {
    type: String,
  },
  icon: {
    type: [Object, Function] as PropType<Component>,
  },
});
</script>

<style lang="scss">
.destination-item {
  .destination-item-icon {
    @apply aspect-square h-auto w-full rounded-full border border-neutral-950/10 dark:border-white/10;

    .image-loader-image {
      @apply box-content;
    }
  }
}
</style>
