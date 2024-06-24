<template>
  <div class="home">
    <div>
      {{ count }} : {{ anotherCount }}
    </div>
    <button @click="count++">Increment</button>
    <button @click="method">print</button>
    <div> {{ person.name }} : {{ person.age }}</div>
    <input v-model="person.name">
    <div> {{ name }}</div>
    <input v-model="name">
    <button @click="submit">addName</button>
    <div>{{ submittedNames }}</div>

    <ul>
      <li
        v-for="subName in submittedNames"
        :key="subName"
      >
        {{ subName }}
      </li>
    </ul>
  </div>
</template>

<script setup>

import { ref } from 'vue';


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

</script>
