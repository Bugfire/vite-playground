<script lang="ts">
import { defineComponent, ref } from 'vue';
import ChildCompositionApi from './ChildCompositionApi.vue';

export default defineComponent({
  components: { ChildCompositionApi },
  setup() {
    const log = ref('');
    const foobar = ref<InstanceType<typeof ChildCompositionApi>>();
    const onClick = () => {
      log.value += 'onClick [ParentComponent]\n';
      log.value += `  child abc=${foobar?.value?.abc}\n`;
      log.value += `  child someMethod => ${foobar?.value?.someMethod()}\n`;
    };
    return { onClick, foobar, log };
  },
});
</script>

<template>
  <div>
    <div>Parent Component</div>
    <button @click="onClick">Button</button>
    <ChildCompositionApi ref="foobar" />
    <pre>{{ log }}</pre>
  </div>
</template>

<style scoped>
pre {
  border: 1px solid lightgray;
  padding: 4px;
}
</style>
