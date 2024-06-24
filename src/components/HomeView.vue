<template>
  <div class="home">
    <div>
      {{ count }} : {{ anotherCount }}
    </div>
    <q-btn @click="count++">Increment</q-btn>
    <q-btn @click="counterStore.increment()">print</q-btn>
    <div class="text-h4 q-ma-xl"> {{ person.name }} : {{ person.age }}</div>
    <input v-model="person.name">
    <div>{{ title }}</div>
    <div>{{ person }}</div>
    <q-input v-model="name" type="text" class="q-ma-sm" />
    <button @click="submit">addName</button>
    <div>{{ submittedNames }} {{ counterStore.doubleCount }}</div>
    <q-list>
      <q-item
        v-for="(subName, index) in submittedNames"
        :key="index"
      >
        <NameItem
          :id="subName"
          :name="subName"
          :item-id="index"
        />
      </q-item>
    </q-list>
  </div>
</template>

<script setup>

import { computed, ref } from 'vue';
import NameItem from 'components/NameItem.vue';
import { useCounterStore } from 'stores/example-store';

const counterStore = useCounterStore();

const count = ref(0);
const name = ref('empty');
const anotherCount = count.value;
const submittedNames = ref(['a', 'b', 'c']);

const method = () => {
  console.log(count);
};

const person = ref({ name: 'John', age: 25 });
const submit = () => {
  submittedNames.value.push(name.value);
  name.value = '';
};

const title = computed(() => `variable name is ${name.value}`);

</script>
