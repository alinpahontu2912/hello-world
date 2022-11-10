/* eslint-disable */
<template>
  <!-- eslint-disable-next-line -->
  <SubmitForm @newPerson="msg => ceva.value = msg" />
  <p>{{ ceva }}</p>
  <DemoGrid :data="gridData" :columns="gridColumns" />
</template>

<script setup>
import SubmitForm from './components/SubmitForm.vue'
import DemoGrid from './components/GridView.vue'

import { ref } from 'vue'
const ceva = ref('test')
const gridColumns = ['Nume', 'Prenume', 'DataNasterii']
const gridData = ref([])
</script>


