<script setup lang="ts">
import {defineComponent, type SlotsType} from 'vue'

const Hello = defineComponent(
  (props, context) => {
    return () =>
      context.slots.content!({
        message: 'Hello world'
      })
  },
  {
    slots: Object as SlotsType<{
      content: { message: string }
    }>
  }
)

const Hello2 = defineComponent({
  slots: Object as SlotsType<{
    content: { message: string }
  }>,
  setup(props, context) {
    return () =>
      context.slots.content({
        message: 'Hello world 2'
      })
  }
})
</script>

<template>
  <Hello>
    <template #content="{ message }">
      <p>{{ message }}</p>
    </template>
  </Hello>
  <Hello2>
    <template #content="{ message }">
      <p>{{ message }}</p>
    </template>
  </Hello2>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
