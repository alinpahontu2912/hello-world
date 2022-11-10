/* eslint-disable */
<template>
  <!-- eslint-disable-next-line -->
  <SubmitForm @test="msg => console.log(msg)" />
  <p>{{ ceva }}</p>
  <DemoGrid :data="gridData" :columns="gridColumns" />
</template>

<script setup>
import SubmitForm from './components/SubmitForm.vue'
import DemoGrid from './components/GridView.vue'

import { ref } from 'vue'
const ceva = ref("dfasdf")
const gridColumns = ['Nume', 'Prenume', 'DataNasterii']
const gridData = ref([])
</script>


