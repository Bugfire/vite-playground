<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  setup() {
    const abc = ref(123);
    const someMethod = () => `someMethod() on [ChildCompositionAPI] abc=${abc.value}`;
    const onClick = () => abc.value++;
    return { abc, someMethod, onClick };
  },
});
</script>

<template>
  <div>Child CompositionAPI</div>
  <button @click="onClick">CountUp {{ abc }}</button>
</template>
