<template>
  <q-item-section>
    <div>
      title: {{ title }} and {{ counterStore.counter }} its id is {{ props.itemId }}
    </div>
    <div>
      {{ counterStore.doubleCount }}
    </div>
    <div>
      <b>it</b> is {{ props.name }}
    </div>
  </q-item-section>
</template>

<script setup>

import { computed } from 'vue';

import { useCounterStore } from 'stores/example-store';

const counterStore = useCounterStore();

const title = computed(() => `variable name is ${props.name}`);

const props = defineProps({
  name: {
    type: String,
    required: true,
    default: 'default name',
  },
  itemId: Number,
});

</script>
